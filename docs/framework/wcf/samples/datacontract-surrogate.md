---
title: DataContract Yedeği
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 10b0c2a3e82e39b03291f567ca360c51042b464e
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342400"
---
# <a name="datacontract-surrogate"></a>DataContract Yedeği
Bu örnek nasıl sınıf serileştirme ve seri durumundan çıkarma, şema dışarı aktarma ve şema içeri aktarma veri anlaşması kullanılarak özelleştirilebilir gibi işlemleri vekil gösterir. Bu örnek senaryoda verilerin serileştirilmiş ve Windows Communication Foundation (WCF) istemci ve hizmet arasında aktarılan bir istemci ve sunucu bir vekil kullanmayı gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örnek, aşağıdaki hizmet sözleşmesini kullanır:  
  
```  
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
  
 `AddEmployee` İşlemi yeni çalışanlar hakkında veri eklemek kullanıcıların sağlar ve `GetEmployee` işlem çalışanları adına göre ara destekler.  
  
 Bu işlemler, aşağıdaki veri türünü kullanın:  
  
```  
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
  
 İçinde `Employee` türü `Person` (Aşağıdaki örnek kodda gösterilmiştir) sınıfı tarafından serileştirilemiyor <xref:System.Runtime.Serialization.DataContractSerializer> geçerli veri sözleşme sınıfı olmadığından.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Uygulayabileceğiniz `DataContract` özniteliğini `Person` sınıfı, ancak bu her zaman mümkün değildir. Örneğin, `Person` sınıfı üzerinde hiçbir denetimi sahip ayrı bir derleme içinde tanımlanabilir.  
  
 Bu kısıtlama, serileştirilecek yollarından biri verilen `Person` sınıftır ile işaretlenmiş başka bir sınıf ile yerine `DataContractAttribute` kopyalayıp yeni bir sınıf için gerekli veriler üzerinde. Hedefi olmasını sağlamaktır `Person` sınıfı görünmesi için bir DataContract olarak <xref:System.Runtime.Serialization.DataContractSerializer>. Bu sınıfları olmayan veri sözleşme seri hale getirmek için bir yol olduğunu unutmayın.  
  
 Örnek mantıksal olarak değiştirir `Person` adlı farklı bir sınıf sınıfıyla `PersonSurrogated`.  
  
```  
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
  
 Veri sözleşmesi vekil bu değiştirme elde etmek için kullanılır. Bir veri anlaşması vekil uygulayan sınıftır <xref:System.Runtime.Serialization.IDataContractSurrogate>. Bu örnekte `AllowNonSerializableTypesSurrogate` sınıfı bu arabirimi uygular.  
  
 Arabirimi uygulama, ilk görevi türü eşleme oluşturmaktır `Person` için `PersonSurrogated`. Bu, hem seri hale getirme zaman yanı sıra şema dışarı aktarma zaman kullanılır. Bu eşleme uygulayarak sağlanır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> yöntemi.  
  
```  
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Yöntemi eşlemeleri bir `Person` için örnek bir `PersonSurrogated` aşağıdaki örnek kodda gösterildiği gibi seri hale getirme sırasında örneği.  
  
```  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Yöntemi, aşağıdaki örnek kodda gösterildiği gibi seri durumundan çıkarma için ters eşleme sağlar.  
  
```  
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
  
 Eşlenecek `PersonSurrogated` veri anlaşması varolan `Person` sırasında şema içeri aktarma, örnek uygulayan sınıf <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> yöntemi, aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
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
  
 Aşağıdaki örnek kod uygulanması tamamlandıktan <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimi.  
  
```  
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
  
 Bu örnekte, temsilci adlı bir öznitelik tarafından ServiceModel içinde etkinleştirilir `AllowNonSerializableTypesAttribute`. Geliştiriciler, bu öznitelik, hizmet sözleşmesini gösterildiği uygulanacak #içeren `IPersonnelDataService` hizmet sözleşmesini yukarıdaki. Bu öznitelik uygulayan `IContractBehavior` ve işlemleri üzerinde vekil ayarlar kendi `ApplyClientBehavior` ve `ApplyDispatchBehavior` yöntemleri.  
  
 Öznitelik, bu durumda gerekli değildir - bu tanıtım amacıyla kullanılır. Kullanıcılar ayrıca etkinleştirebilir bir vekil el ile benzer bir ekleyerek `IContractBehavior`, `IEndpointBehavior` veya `IOperationBehavior` kod veya yapılandırma kullanarak.  
  
 `IContractBehavior` Uygulama varsa bunlar denetleyerek DataContract kullanan işlemleri arar bir `DataContractSerializerOperationBehavior` kayıtlı. Eğer öyleyse, bu ayarlar `DataContractSurrogate` bu davranışı özelliği. Aşağıdaki örnek kod, nasıl yapıldığını gösterir. Bu işlemin davranışını vekil ayarlamak, serileştirme ve seri durumundan çıkarma için sağlar.  
  
```  
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
  
 Meta verileri oluşturma sırasında kullanmak için yedek takın ek adımlar gerekir. Bunu yapmak için bir mekanizmadır sağlamak için bir `IWsdlExportExtension` olduğu ne Bu örnek gösterir. Değiştirmek için başka bir yoludur `WsdlExporter` doğrudan.  
  
 `AllowNonSerializableTypesAttribute` Özniteliğini uygular `IWsdlExportExtension` ve `IContractBehavior`. Uzantı olabilir bir `IContractBehavior` veya `IEndpointBehavior` böyle bir durumda. Kendi `IWsdlExportExtension.ExportContract` yöntem uygulamasını sağlar vekil ekleyerek `XsdDataContractExporter` DataContract için şema oluşturma sırasında kullanılır. Aşağıdaki kod parçacığı, bunun nasıl yapılacağı gösterilmektedir.  
  
```  
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
  
 Örneği çalıştırdığında istemci ilk çağrı başarılı olup olmadığını denetlemek için GetEmployee çağrısı tarafından izlenen AddEmployee çağırır. GetEmployee işlemi isteğinin sonucunu istemci konsol penceresinde görüntülenir. GetEmployee işlemi, çalışan bulma konusunda başarılı ve "bulunamadı" yazdırın.  
  
> [!NOTE]
>  Bu örnek, seri durumdan nasıl serileştirme için bir yedek takın ve meta verileri oluşturmayı gösterir. Meta verilerden kod oluşturma için bir yedek takmak nasıl algılanacağını göstermez. İstemci kodu oluşturma eklenebilecek bir vekil'ın nasıl kullanılabileceğini, bir örnek görmek için [özel WSDL yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) örnek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  C# sürümü çözümü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a>Ayrıca Bkz.
