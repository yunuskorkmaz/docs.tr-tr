---
title: DataContract Yedeği
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 9677e3cf024e6c1e5b2f3360423ab55536748495
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600055"
---
# <a name="datacontract-surrogate"></a>DataContract Yedeği
Bu örnek, bir veri sözleşmesi yedek sınıfı kullanılarak serileştirme, seri durumdan çıkarma, şema dışarı aktarma ve şema içeri aktarma gibi işlemlerin nasıl özelleştirilebileceğini gösterir. Bu örnek, verilerin serileştirildiği ve bir Windows Communication Foundation (WCF) istemci ve hizmeti arasında aktarıldığı bir istemci ve sunucu senaryosunda bir vekil 'in nasıl kullanılacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek, aşağıdaki hizmet sözleşmesini kullanır:  
  
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
  
 `AddEmployee`İşlem, kullanıcıların yeni çalışanlar hakkında veri eklemesine izin verir ve `GetEmployee` işlem, ad temelinde çalışanları aramayı destekler.  
  
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
  
 `Employee`Türünde, `Person` Sınıf (Aşağıdaki örnek kodda gösterilen), <xref:System.Runtime.Serialization.DataContractSerializer> geçerli bir veri sözleşmesi sınıfı olmadığından tarafından serileştirilemiyor.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <xref:System.Runtime.Serialization.DataContractAttribute>Özniteliğini `Person` sınıfına uygulayabilirsiniz, ancak bu her zaman mümkün değildir. Örneğin, sınıfı, `Person` denetiminiz olmayan ayrı bir derlemede tanımlanabilir.  
  
 Bu kısıtlama verildiğinde, sınıfı seri hale getirmenin bir yolu, öğesini `Person` ile işaretlenen başka bir sınıfla yerine <xref:System.Runtime.Serialization.DataContractAttribute> Yeni sınıfa, gerekli verilerin üzerine kopyalamasıdır. Amaç, `Person` sınıfın bir DataContract olarak görünmesini sağlar <xref:System.Runtime.Serialization.DataContractSerializer> . Bu, veri olmayan sözleşme sınıflarını serileştirmenin bir yoludur.  
  
 Örnek, `Person` sınıfının adlı farklı bir sınıfla mantıksal olarak yerini alır `PersonSurrogated` .  
  
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
  
 Bu değişikliği başarmak için veri sözleşmesi yedeği kullanılır. Veri anlaşması yedeği, uygulayan bir sınıftır <xref:System.Runtime.Serialization.IDataContractSurrogate> . Bu örnekte, `AllowNonSerializableTypesSurrogate` sınıfı bu arabirimi uygular.  
  
 Arabirim uygulamasında ilk görev, öğesinden öğesine bir tür eşlemesi oluşturmak için kullanılır `Person` `PersonSurrogated` . Bu, hem serileştirme zamanında hem de şema dışa aktarma zamanında kullanılır. Bu eşleme yöntemi uygulayarak elde edilir <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> .  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29>Yöntemi, `Person` `PersonSurrogated` Aşağıdaki örnek kodda gösterildiği gibi serileştirme sırasında bir örneği bir örneğe eşler.  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29>Yöntemi, aşağıdaki örnek kodda gösterildiği gibi, seri durumdan çıkarma için ters eşlemeyi sağlar.  
  
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
  
 `PersonSurrogated`Şema içeri aktarma sırasında veri sözleşmesini varolan sınıfla eşlemek için, `Person` örneği <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> Aşağıdaki örnek kodda gösterildiği gibi yöntemini uygular.  
  
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
  
 Aşağıdaki örnek kod, arabiriminin uygulamasını tamamlar <xref:System.Runtime.Serialization.IDataContractSurrogate> .  
  
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
  
 Bu örnekte, yedek, ServiceModel içinde adlı bir öznitelik tarafından etkinleştirilir `AllowNonSerializableTypesAttribute` . Geliştiricilerin, yukarıdaki hizmet sözleşmesinde gösterildiği gibi bu özniteliği hizmet sözleşmelerine uygulaması gerekir `IPersonnelDataService` . Bu öznitelik `IContractBehavior` , ve yöntemlerinde işlemleri uygular ve üzerinde yedek ayarlar `ApplyClientBehavior` `ApplyDispatchBehavior` .  
  
 Bu örnekte öznitelik gerekli değildir-bu örnekteki tanıtım amaçlarıyla kullanılır. Kullanıcılar ayrıca, el ile benzer `IContractBehavior` `IEndpointBehavior` veya `IOperationBehavior` kod kullanarak ya da yapılandırma kullanarak bir yedeği etkinleştirebilir.  
  
 `IContractBehavior`Uygulama, kayıtlı olup olmadığını denetleyerek DataContract kullanan işlemlere bakar `DataContractSerializerOperationBehavior` . Bu durumda, `DataContractSurrogate` özelliği o davranışa ayarlar. Aşağıdaki örnek kod, bunun nasıl yapıldığını göstermektedir. Bu işlem davranışında yedeği ayarlamak, serileştirme ve seri durumdan çıkarma için izin vermez.  
  
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
  
 Meta veri oluşturma sırasında kullanılmak üzere yedeği eklemek için ek adımların alınması gerekir. Bunu yapmak için bir mekanizma, `IWsdlExportExtension` Bu örneğin gösterdiği şeydir. Başka bir yol da doğrudan değiştirmektir `WsdlExporter` .  
  
 `AllowNonSerializableTypesAttribute`Özniteliği ve uygular `IWsdlExportExtension` `IContractBehavior` . Uzantı ya da `IContractBehavior` `IEndpointBehavior` Bu durumda olabilir. `IWsdlExportExtension.ExportContract`Yöntem uygulama, `XsdDataContractExporter` DataContract için şema oluşturma sırasında kullanılan öğesine ekleyerek yedeği sağlar. Aşağıdaki kod parçacığında bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 Örneği çalıştırdığınızda, istemci, ilk çağrının başarılı olup olmadığını denetlemek için bir GetEmployee çağrısı tarafından izlenen AddEmployee öğesini çağırır. GetEmployee işlem isteğinin sonucu istemci konsol penceresinde görüntülenir. GetEmployee işlemi, çalışanı bulma ve "Found" Yazdırma işleminde başarılı olmalıdır.  
  
> [!NOTE]
> Bu örnek, seri hale getirme, seri durumdan çıkarma ve meta veri oluşturma için bir vekil nasıl ekleneceğini gösterir. Meta verilerden kod üretimi için bir yedeği nasıl bir fişe ekleneceğini göstermez. Bir vekil 'in istemci kod üretimini eklemek için nasıl kullanılabileceği hakkında bir örnek görmek için bkz. [özel wsdl yayınlama](custom-wsdl-publication.md) örneği.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# sürümünü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
