---
title: DataContract Yedeği
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 7ef78c4361c055d7be35c03a3c8717e86aceddab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183829"
---
# <a name="datacontract-surrogate"></a>DataContract Yedeği
Bu örnek, serileştirme, deserialization, şema dışa aktarma ve şema alma gibi işlemlerin bir veri sözleşmesi vekil sınıfı kullanılarak nasıl özelleştirilebildiğini göstermektedir. Bu örnek, verilerin serihale edildiği ve Windows Communication Foundation (WCF) istemcisi (WCF) istemcisi ile hizmeti arasında aktarıldığı bir istemci ve sunucu senaryosunda bir vekilin nasıl kullanılacağını gösterir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnekte aşağıdaki hizmet sözleşmesi kullanır:  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 İşlem, `AddEmployee` kullanıcıların yeni çalışanlar hakkında veri `GetEmployee` eklemesine olanak tanır ve işlem, ada göre çalışan aramasını destekler.  
  
 Bu işlemler aşağıdaki veri türünü kullanır:  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 `Employee` Türde, `Person` geçerli bir veri sözleşmesi sınıfı olmadığı için sınıf (aşağıdaki örnek kodda gösterilmiştir) tarafından <xref:System.Runtime.Serialization.DataContractSerializer> serileştirilemez.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Özniteliği <xref:System.Runtime.Serialization.DataContractAttribute> `Person` sınıfa uygulayabilirsiniz, ancak bu her zaman mümkün değildir. Örneğin, `Person` sınıf üzerinde hiçbir denetimi olmayan ayrı bir derleme tanımlanabilir.  
  
 Bu kısıtlama göz önüne alındığında, `Person` sınıfı serihale etmenin bir yolu, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfı işaretlenmiş başka bir sınıfla değiştirmek ve gerekli veriler üzerinden yeni sınıfa kopyalamaktır. Amaç, `Person` sınıfın Bir DataContract olarak görünmesini <xref:System.Runtime.Serialization.DataContractSerializer>sağlamaktır. Bunun veri dışı sözleşme sınıflarını seri hale getirmek için bir yol olduğunu unutmayın.  
  
 Örnek mantıksal olarak `Person` sınıfı farklı bir sınıf `PersonSurrogated`adlandırılmış sınıfla değiştirir.  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 Veri sözleşmesi vekil bu değiştirme elde etmek için kullanılır. Veri sözleşmesi nin sureti, <xref:System.Runtime.Serialization.IDataContractSurrogate>'yi uygulayan bir sınıftır. Bu örnekte, `AllowNonSerializableTypesSurrogate` sınıf bu arabirimi uygular.  
  
 Arabirim uygulamasında, ilk görev `Person` `PersonSurrogated`bir tür eşleme oluşturmaktır. Bu hem serileştirme zamanında hem de şema dışa aktarma zamanında kullanılır. Bu eşleme <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> yöntemi uygulanarak elde edilir.  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 Yöntem, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> aşağıdaki `Person` örnek `PersonSurrogated` kodda gösterildiği gibi, bir örneği serileştirme sırasındaki bir örnekle eşler.  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 Yöntem, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> aşağıdaki örnek kodda gösterildiği gibi, deserialization için ters eşleme sağlar.  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 `PersonSurrogated` Şema alma sırasında veri `Person` sözleşmesini varolan sınıfla eşlemek <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> için, örnek aşağıdaki örnek kodda gösterildiği gibi yöntemi uygular.  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 Aşağıdaki örnek kod <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimin uygulanmasını tamamlar.  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 Bu örnekte, vekil ServiceModel'de . `AllowNonSerializableTypesAttribute` Geliştiricilerin bu özniteliği, yukarıdaki hizmet sözleşmesinde `IPersonnelDataService` gösterildiği gibi hizmet sözleşmesinde uygulamaları gerekir. Bu öznitelik `IContractBehavior` uygular ve kendi `ApplyClientBehavior` ve `ApplyDispatchBehavior` yöntemleri işlemleri üzerinde vekil kurar.  
  
 Bu durumda öznitelik gerekli değildir - bu örnekte gösteri amacıyla kullanılır. Kullanıcılar alternatif olarak benzer `IContractBehavior`bir madde ekleyerek `IEndpointBehavior` veya `IOperationBehavior` kodu kullanarak veya yapılandırmayı kullanarak bir vekil etkinleştirebilir.  
  
 Uygulama, `IContractBehavior` `DataContractSerializerOperationBehavior` kayıtlı olup olmadıklarını denetleyerek DataContract kullanan işlemleri arar. Eğer yaparlarsa, `DataContractSurrogate` bu davranış özelliği ayarlar. Aşağıdaki örnek kod, bunun nasıl yapıldığını gösterir. Bu işlem davranışı üzerinde vekil ayarı serileştirme ve deserialization için sağlar.  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 Meta veri oluşturma sırasında kullanılmak üzere vekil takmak için ek adımlar atılması gerekir. Bunu yapmak için bir mekanizma, bu örnek ne gösterir bir `IWsdlExportExtension` sağlamaktır. Başka bir yolu `WsdlExporter` doğrudan değiştirmektir.  
  
 Öznitelik `AllowNonSerializableTypesAttribute` uygular `IWsdlExportExtension` ve `IContractBehavior`. Uzantı bir `IContractBehavior` veya `IEndpointBehavior` bu durumda olabilir. Yöntem `IWsdlExportExtension.ExportContract` uygulaması, DataContract için şema `XsdDataContractExporter` üretimi sırasında kullanılana ekleyerek vekilin kullanılmasını sağlar. Aşağıdaki kod parçacığı bunun nasıl yapılacağını gösterir.  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 Örneği çalıştırdığınızda, istemci AddEmployee'ı çağırır ve ardından ilk çağrının başarılı olup olmadığını kontrol etmek için GetEmployee çağrısını alır. GetEmployee işlem isteğinin sonucu istemci konsol penceresinde görüntülenir. GetEmployee işlemi, çalışanBulma ve "bulunan" yazdırma başarılı olmalıdır.  
  
> [!NOTE]
> Bu örnek, serihale, deserialize ve meta veri üretimi için bir vekil nasıl takTı gösterilmektedir. Meta verilerden kod oluşturma için bir vekilnasıl takılsüreceğini göstermez. Bir vekilin istemci kodu oluşturmaya takmak için nasıl kullanılabileceğini görmek için [Özel WSDL Yayın](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) örneğine bakın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# sürümünü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
