---
title: DataContract Yedeği
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: a56fbcabfacf146142f7b0c0623325cc8e69c29a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769105"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="67315-102">DataContract Yedeği</span><span class="sxs-lookup"><span data-stu-id="67315-102">DataContract Surrogate</span></span>
<span data-ttu-id="67315-103">Bu örnek nasıl sınıf serileştirme ve seri durumundan çıkarma, şema dışarı aktarma ve şema içeri aktarma veri anlaşması kullanılarak özelleştirilebilir gibi işlemleri vekil gösterir.</span><span class="sxs-lookup"><span data-stu-id="67315-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="67315-104">Bu örnek senaryoda verilerin serileştirilmiş ve Windows Communication Foundation (WCF) istemci ve hizmet arasında aktarılan bir istemci ve sunucu bir vekil kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="67315-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67315-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="67315-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="67315-106">Örnek, aşağıdaki hizmet sözleşmesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="67315-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="67315-107">`AddEmployee` İşlemi yeni çalışanlar hakkında veri eklemek kullanıcıların sağlar ve `GetEmployee` işlem çalışanları adına göre ara destekler.</span><span class="sxs-lookup"><span data-stu-id="67315-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="67315-108">Bu işlemler, aşağıdaki veri türünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="67315-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="67315-109">İçinde `Employee` türü `Person` (Aşağıdaki örnek kodda gösterilmiştir) sınıfı tarafından serileştirilemiyor <xref:System.Runtime.Serialization.DataContractSerializer> geçerli veri sözleşme sınıfı olmadığından.</span><span class="sxs-lookup"><span data-stu-id="67315-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="67315-110">Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini `Person` sınıfı, ancak bu her zaman mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="67315-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="67315-111">Örneğin, `Person` sınıfı üzerinde hiçbir denetimi sahip ayrı bir derleme içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="67315-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="67315-112">Bu kısıtlama, serileştirilecek yollarından biri verilen `Person` sınıftır ile işaretlenmiş başka bir sınıf ile yerine <xref:System.Runtime.Serialization.DataContractAttribute> kopyalayıp yeni bir sınıf için gerekli veriler üzerinde.</span><span class="sxs-lookup"><span data-stu-id="67315-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="67315-113">Hedefi olmasını sağlamaktır `Person` sınıfı görünmesi için bir DataContract olarak <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="67315-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="67315-114">Bu sınıfları olmayan veri sözleşme seri hale getirmek için bir yol olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="67315-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="67315-115">Örnek mantıksal olarak değiştirir `Person` adlı farklı bir sınıf sınıfıyla `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="67315-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="67315-116">Veri sözleşmesi vekil bu değiştirme elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67315-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="67315-117">Bir veri anlaşması vekil uygulayan sınıftır <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="67315-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="67315-118">Bu örnekte `AllowNonSerializableTypesSurrogate` sınıfı bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="67315-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="67315-119">Arabirimi uygulama, ilk görevi türü eşleme oluşturmaktır `Person` için `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="67315-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="67315-120">Bu, hem seri hale getirme zaman yanı sıra şema dışarı aktarma zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67315-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="67315-121">Bu eşleme uygulayarak sağlanır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67315-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="67315-122"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Yöntemi eşlemeleri bir `Person` için örnek bir `PersonSurrogated` aşağıdaki örnek kodda gösterildiği gibi seri hale getirme sırasında örneği.</span><span class="sxs-lookup"><span data-stu-id="67315-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="67315-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Yöntemi, aşağıdaki örnek kodda gösterildiği gibi seri durumundan çıkarma için ters eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="67315-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="67315-124">Eşlenecek `PersonSurrogated` veri anlaşması varolan `Person` sırasında şema içeri aktarma, örnek uygulayan sınıf <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> yöntemi, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="67315-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="67315-125">Aşağıdaki örnek kod uygulanması tamamlandıktan <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="67315-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="67315-126">Bu örnekte, temsilci adlı bir öznitelik tarafından ServiceModel içinde etkinleştirilir `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="67315-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="67315-127">Geliştiriciler, bu öznitelik, hizmet sözleşmesini gösterildiği uygulanacak #içeren `IPersonnelDataService` hizmet sözleşmesini yukarıdaki.</span><span class="sxs-lookup"><span data-stu-id="67315-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="67315-128">Bu öznitelik uygulayan `IContractBehavior` ve işlemleri üzerinde vekil ayarlar kendi `ApplyClientBehavior` ve `ApplyDispatchBehavior` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="67315-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="67315-129">Öznitelik, bu durumda gerekli değildir - bu tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67315-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="67315-130">Kullanıcılar ayrıca etkinleştirebilir bir vekil el ile benzer bir ekleyerek `IContractBehavior`, `IEndpointBehavior` veya `IOperationBehavior` kod veya yapılandırma kullanarak.</span><span class="sxs-lookup"><span data-stu-id="67315-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="67315-131">`IContractBehavior` Uygulama varsa bunlar denetleyerek DataContract kullanan işlemleri arar bir `DataContractSerializerOperationBehavior` kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="67315-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="67315-132">Eğer öyleyse, bu ayarlar `DataContractSurrogate` bu davranışı özelliği.</span><span class="sxs-lookup"><span data-stu-id="67315-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="67315-133">Aşağıdaki örnek kod, nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67315-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="67315-134">Bu işlemin davranışını vekil ayarlamak, serileştirme ve seri durumundan çıkarma için sağlar.</span><span class="sxs-lookup"><span data-stu-id="67315-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="67315-135">Meta verileri oluşturma sırasında kullanmak için yedek takın ek adımlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="67315-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="67315-136">Bunu yapmak için bir mekanizmadır sağlamak için bir `IWsdlExportExtension` olduğu ne Bu örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="67315-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="67315-137">Değiştirmek için başka bir yoludur `WsdlExporter` doğrudan.</span><span class="sxs-lookup"><span data-stu-id="67315-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="67315-138">`AllowNonSerializableTypesAttribute` Özniteliğini uygular `IWsdlExportExtension` ve `IContractBehavior`.</span><span class="sxs-lookup"><span data-stu-id="67315-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="67315-139">Uzantı olabilir bir `IContractBehavior` veya `IEndpointBehavior` böyle bir durumda.</span><span class="sxs-lookup"><span data-stu-id="67315-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="67315-140">Kendi `IWsdlExportExtension.ExportContract` yöntem uygulamasını sağlar vekil ekleyerek `XsdDataContractExporter` DataContract için şema oluşturma sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67315-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="67315-141">Aşağıdaki kod parçacığı, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67315-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="67315-142">Örneği çalıştırdığında istemci ilk çağrı başarılı olup olmadığını denetlemek için GetEmployee çağrısı tarafından izlenen AddEmployee çağırır.</span><span class="sxs-lookup"><span data-stu-id="67315-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="67315-143">GetEmployee işlemi isteğinin sonucunu istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="67315-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="67315-144">GetEmployee işlemi, çalışan bulma konusunda başarılı ve "bulunamadı" yazdırın.</span><span class="sxs-lookup"><span data-stu-id="67315-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67315-145">Bu örnek, seri durumdan nasıl serileştirme için bir yedek takın ve meta verileri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="67315-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="67315-146">Meta verilerden kod oluşturma için bir yedek takmak nasıl algılanacağını göstermez.</span><span class="sxs-lookup"><span data-stu-id="67315-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="67315-147">İstemci kodu oluşturma eklenebilecek bir vekil'ın nasıl kullanılabileceğini, bir örnek görmek için [özel WSDL yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="67315-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="67315-148">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="67315-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="67315-149">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67315-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="67315-150">C# sürümü çözümü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67315-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="67315-151">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67315-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="67315-152">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="67315-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="67315-153">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="67315-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="67315-154">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="67315-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67315-155">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="67315-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
