---
title: DataContract Yedeği
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 3fd2bf028ccb2f75210d5e3fc039bdad7e1e065a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507869"
---
# <a name="datacontract-surrogate"></a>DataContract Yedeği
Bu örnek nasıl seri hale getirme ve seri durumdan çıkarma, şema verme ve şema alma veri sözleşmesi kullanılarak özelleştirilebilir gibi işlemleri sınıfı vekil gösterir. Bu örnek senaryoda burada veri seri hale getirilmiş ve bir Windows Communication Foundation (WCF) istemci ile hizmet arasında aktarılan bir istemci ve sunucu bir yedek kullanmayı gösterir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnek aşağıdaki hizmet sözleşmesi kullanır:  
  
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
  
 `AddEmployee` İşlemi kullanıcıların yeni çalışanlar hakkındaki verileri eklemesine olanak sağlar ve `GetEmployee` işlemi çalışanları adına göre ara destekler.  
  
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
  
 İçinde `Employee` türü, `Person` (Aşağıdaki örnek kodda gösterildiği) sınıfı seri hale getirilemiyor tarafından <xref:System.Runtime.Serialization.DataContractSerializer> geçerli veri sözleşme sınıfı olmadığından.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Uygulayabileceğiniz `DataContract` özniteliğini `Person` sınıfı, ancak bu her zaman mümkün değildir. Örneğin, `Person` sınıfı üzerinde hiçbir denetimi elinizde ayrı bir derlemede tanımlanmış.  
  
 Bu kısıtlama, bir seri hale getirmek için yolu verilen `Person` sınıftır ile işaretlenen başka bir sınıf değiştirmeyi `DataContractAttribute` ve yeni sınıfı için gerekli verileri üzerinden kopyalayın. Amaç yapmaktır `Person` sınıfı görünür bir DataContract olarak <xref:System.Runtime.Serialization.DataContractSerializer>. Bu veri dışı sözleşme sınıfları serileştirmek için bir yolu olmadığını unutmayın.  
  
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
  
 Veri sözleşmesi yedek bu değiştirme elde etmek için kullanılır. Bir veri sözleşmesi yedek uygulayan bir sınıftır <xref:System.Runtime.Serialization.IDataContractSurrogate>. Bu örnekte `AllowNonSerializableTypesSurrogate` sınıfı bu arabirimi uygular.  
  
 Arabirim uygulamasına ilk görev türü eşlemesinden belirtmektir `Person` için `PersonSurrogated`. Bu, hem seri hale getirme zaman yanı sıra şema verme zaman kullanılır. Bu eşleme uygulayarak elde edilen <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> yöntemi.  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Yöntemi, aşağıdaki örnek kodda gösterildiği gibi seri durumdan çıkarma, geriye doğru eşlemesi sağlar.  
  
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
  
 Eşlemek için `PersonSurrogated` veri sözleşmesi varolan `Person` sırasında şema alma, örnek uygulayan sınıf <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> aşağıdaki örnek kodda gösterildiği gibi yöntemi.  
  
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
  
 Bu örnekte, yedek olarak adlandırılan bir öznitelik tarafından ServiceModel içinde etkinleştirilir `AllowNonSerializableTypesAttribute`. Geliştiricilerin bu öznitelik üzerinde gösterildiği gibi kendi hizmet sözleşmesini uygulama gerekir `IPersonnelDataService` hizmet sözleşmesini yukarıdaki. Bu öznitelik uygulayan `IContractBehavior` ve işlemlerini yedek ayarlar kendi `ApplyClientBehavior` ve `ApplyDispatchBehavior` yöntemleri.  
  
 Öznitelik bu durumda gerekli değildir - bu örnekteki tanıtım amacıyla kullanılır. Kullanıcılar ayrıca etkinleştirebilir bir yedek el ile benzer ekleyerek `IContractBehavior`, `IEndpointBehavior` veya `IOperationBehavior` kod veya yapılandırma kullanarak.  
  
 `IContractBehavior` Bunlar varsa denetleyerek DataContract kullanan işlemler arar uygulaması bir `DataContractSerializerOperationBehavior` kayıtlı. İçermiyorlarsa ayarlar `DataContractSurrogate` bu davranışı özelliği. Aşağıdaki örnek kod, bunun nasıl yapılacağı gösterilmektedir. Yedek üzerinde bu işlemi davranışı ayarlama, seri hale getirme ve seri durumundan çıkarma için etkinleştirir.  
  
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
  
 Yedek meta veri oluşturma sırasında kullanılacak takın ulaşmak ek adımlar gerekir. Bunu yapmak için bir mekanizmadır sağlamak için bir `IWsdlExportExtension` olduğu ne Bu örnek gösterilmektedir. Değiştirmek için başka bir yoldur `WsdlExporter` doğrudan.  
  
 `AllowNonSerializableTypesAttribute` Özniteliği uygulayan `IWsdlExportExtension` ve `IContractBehavior`. Uzantısı ya da olabilir bir `IContractBehavior` veya `IEndpointBehavior` bu durumda. Kendi `IWsdlExportExtension.ExportContract` yöntem uygulaması ekleyerek yedek etkinleştirir `XsdDataContractExporter` DataContract için şema oluşturma sırasında kullanılır. Aşağıdaki kod parçacığını bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 Örneği çalıştırdığınızda, istemci ilk çağrı başarılı olup olmadığını denetlemek için GetEmployee çağrısı tarafından izlenen AddEmployee çağırır. GetEmployee işlemi isteğinin sonucunu istemci konsol penceresinde görüntülenir. GetEmployee işlemi çalışan bulma başarılı ve "bulunamadı" yazdırma gerekir.  
  
> [!NOTE]
>  Bu örnek nasıl serileştirme için bir yedek takın, seri durumdan ve meta verileri oluşturma göstermektedir. Kod oluşturma meta veriler için bir yedek takın nasıl göstermez. İstemci kodu oluşturma takmak için bir yedek'ın nasıl kullanılabileceğini, bir örnek görmek için [özel WSDL yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) örnek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  C# sürümü çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a>Ayrıca Bkz.
