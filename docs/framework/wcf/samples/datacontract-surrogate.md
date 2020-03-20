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
# <a name="datacontract-surrogate"></a><span data-ttu-id="fc605-102">DataContract Yedeği</span><span class="sxs-lookup"><span data-stu-id="fc605-102">DataContract Surrogate</span></span>
<span data-ttu-id="fc605-103">Bu örnek, serileştirme, deserialization, şema dışa aktarma ve şema alma gibi işlemlerin bir veri sözleşmesi vekil sınıfı kullanılarak nasıl özelleştirilebildiğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fc605-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="fc605-104">Bu örnek, verilerin serihale edildiği ve Windows Communication Foundation (WCF) istemcisi (WCF) istemcisi ile hizmeti arasında aktarıldığı bir istemci ve sunucu senaryosunda bir vekilin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc605-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc605-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="fc605-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fc605-106">Örnekte aşağıdaki hizmet sözleşmesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="fc605-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="fc605-107">İşlem, `AddEmployee` kullanıcıların yeni çalışanlar hakkında veri `GetEmployee` eklemesine olanak tanır ve işlem, ada göre çalışan aramasını destekler.</span><span class="sxs-lookup"><span data-stu-id="fc605-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="fc605-108">Bu işlemler aşağıdaki veri türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="fc605-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="fc605-109">`Employee` Türde, `Person` geçerli bir veri sözleşmesi sınıfı olmadığı için sınıf (aşağıdaki örnek kodda gösterilmiştir) tarafından <xref:System.Runtime.Serialization.DataContractSerializer> serileştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fc605-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="fc605-110">Özniteliği <xref:System.Runtime.Serialization.DataContractAttribute> `Person` sınıfa uygulayabilirsiniz, ancak bu her zaman mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="fc605-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="fc605-111">Örneğin, `Person` sınıf üzerinde hiçbir denetimi olmayan ayrı bir derleme tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fc605-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="fc605-112">Bu kısıtlama göz önüne alındığında, `Person` sınıfı serihale etmenin bir yolu, <xref:System.Runtime.Serialization.DataContractAttribute> sınıfı işaretlenmiş başka bir sınıfla değiştirmek ve gerekli veriler üzerinden yeni sınıfa kopyalamaktır.</span><span class="sxs-lookup"><span data-stu-id="fc605-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="fc605-113">Amaç, `Person` sınıfın Bir DataContract olarak görünmesini <xref:System.Runtime.Serialization.DataContractSerializer>sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fc605-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="fc605-114">Bunun veri dışı sözleşme sınıflarını seri hale getirmek için bir yol olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fc605-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="fc605-115">Örnek mantıksal olarak `Person` sınıfı farklı bir sınıf `PersonSurrogated`adlandırılmış sınıfla değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fc605-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="fc605-116">Veri sözleşmesi vekil bu değiştirme elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc605-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="fc605-117">Veri sözleşmesi nin sureti, <xref:System.Runtime.Serialization.IDataContractSurrogate>'yi uygulayan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fc605-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="fc605-118">Bu örnekte, `AllowNonSerializableTypesSurrogate` sınıf bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="fc605-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="fc605-119">Arabirim uygulamasında, ilk görev `Person` `PersonSurrogated`bir tür eşleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="fc605-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="fc605-120">Bu hem serileştirme zamanında hem de şema dışa aktarma zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc605-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="fc605-121">Bu eşleme <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> yöntemi uygulanarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="fc605-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="fc605-122">Yöntem, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> aşağıdaki `Person` örnek `PersonSurrogated` kodda gösterildiği gibi, bir örneği serileştirme sırasındaki bir örnekle eşler.</span><span class="sxs-lookup"><span data-stu-id="fc605-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="fc605-123">Yöntem, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> aşağıdaki örnek kodda gösterildiği gibi, deserialization için ters eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc605-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="fc605-124">`PersonSurrogated` Şema alma sırasında veri `Person` sözleşmesini varolan sınıfla eşlemek <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> için, örnek aşağıdaki örnek kodda gösterildiği gibi yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="fc605-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="fc605-125">Aşağıdaki örnek kod <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimin uygulanmasını tamamlar.</span><span class="sxs-lookup"><span data-stu-id="fc605-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="fc605-126">Bu örnekte, vekil ServiceModel'de . `AllowNonSerializableTypesAttribute`</span><span class="sxs-lookup"><span data-stu-id="fc605-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="fc605-127">Geliştiricilerin bu özniteliği, yukarıdaki hizmet sözleşmesinde `IPersonnelDataService` gösterildiği gibi hizmet sözleşmesinde uygulamaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc605-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="fc605-128">Bu öznitelik `IContractBehavior` uygular ve kendi `ApplyClientBehavior` ve `ApplyDispatchBehavior` yöntemleri işlemleri üzerinde vekil kurar.</span><span class="sxs-lookup"><span data-stu-id="fc605-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="fc605-129">Bu durumda öznitelik gerekli değildir - bu örnekte gösteri amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc605-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="fc605-130">Kullanıcılar alternatif olarak benzer `IContractBehavior`bir madde ekleyerek `IEndpointBehavior` veya `IOperationBehavior` kodu kullanarak veya yapılandırmayı kullanarak bir vekil etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fc605-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="fc605-131">Uygulama, `IContractBehavior` `DataContractSerializerOperationBehavior` kayıtlı olup olmadıklarını denetleyerek DataContract kullanan işlemleri arar.</span><span class="sxs-lookup"><span data-stu-id="fc605-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="fc605-132">Eğer yaparlarsa, `DataContractSurrogate` bu davranış özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fc605-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="fc605-133">Aşağıdaki örnek kod, bunun nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc605-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="fc605-134">Bu işlem davranışı üzerinde vekil ayarı serileştirme ve deserialization için sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc605-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="fc605-135">Meta veri oluşturma sırasında kullanılmak üzere vekil takmak için ek adımlar atılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc605-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="fc605-136">Bunu yapmak için bir mekanizma, bu örnek ne gösterir bir `IWsdlExportExtension` sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fc605-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="fc605-137">Başka bir yolu `WsdlExporter` doğrudan değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="fc605-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="fc605-138">Öznitelik `AllowNonSerializableTypesAttribute` uygular `IWsdlExportExtension` ve `IContractBehavior`.</span><span class="sxs-lookup"><span data-stu-id="fc605-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="fc605-139">Uzantı bir `IContractBehavior` veya `IEndpointBehavior` bu durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc605-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="fc605-140">Yöntem `IWsdlExportExtension.ExportContract` uygulaması, DataContract için şema `XsdDataContractExporter` üretimi sırasında kullanılana ekleyerek vekilin kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc605-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="fc605-141">Aşağıdaki kod parçacığı bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc605-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="fc605-142">Örneği çalıştırdığınızda, istemci AddEmployee'ı çağırır ve ardından ilk çağrının başarılı olup olmadığını kontrol etmek için GetEmployee çağrısını alır.</span><span class="sxs-lookup"><span data-stu-id="fc605-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="fc605-143">GetEmployee işlem isteğinin sonucu istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc605-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="fc605-144">GetEmployee işlemi, çalışanBulma ve "bulunan" yazdırma başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc605-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc605-145">Bu örnek, serihale, deserialize ve meta veri üretimi için bir vekil nasıl takTı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc605-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="fc605-146">Meta verilerden kod oluşturma için bir vekilnasıl takılsüreceğini göstermez.</span><span class="sxs-lookup"><span data-stu-id="fc605-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="fc605-147">Bir vekilin istemci kodu oluşturmaya takmak için nasıl kullanılabileceğini görmek için [Özel WSDL Yayın](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="fc605-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc605-148">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fc605-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fc605-149">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc605-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fc605-150">Çözümün C# sürümünü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc605-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fc605-151">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc605-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc605-152">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc605-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc605-153">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fc605-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fc605-154">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="fc605-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc605-155">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc605-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
