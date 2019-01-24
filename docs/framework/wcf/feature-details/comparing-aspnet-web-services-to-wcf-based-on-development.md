---
title: ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: 6bf9743410d3138efd5f3ea151b58f61e46ef683
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496799"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="fdc10-102">ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fdc10-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
<span data-ttu-id="fdc10-103">Windows Communication Foundation (WCF) WCF programlanmış ve ASP.NET Web Hizmetleri gibi yapılandırılmış uygulamaların sağlar ve davranışlarını taklit etmek için ASP.NET uyumluluk modu seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="fdc10-104">Aşağıdaki bölümlerde ASP.NET Web hizmetlerini karşılaştırın ve WCF ne hem teknolojiler kullanarak uygulama geliştirmek için gerekli olduğuna bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="fdc10-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="fdc10-105">Veri gösterimi</span><span class="sxs-lookup"><span data-stu-id="fdc10-105">Data Representation</span></span>  
 <span data-ttu-id="fdc10-106">Bir Web hizmeti ASP.NET ile geliştirme genellikle hizmet kullanmaktır herhangi bir karmaşık veri türlerini tanımlama ile başlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="fdc10-107">ASP.NET dayanır <xref:System.Xml.Serialization.XmlSerializer> iletilmesi için veya bir hizmet için XML .NET Framework türleri tarafından temsil edilen veri Çevir ve .NET Framework nesnelerini XML olarak alınan veriler çevir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="fdc10-108">ASP.NET hizmeti kullanmaktır karmaşık veri türlerini tanımlanmasını gerektirir tanımını .NET Framework sınıfları <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden serileştirebiliyorsa.</span><span class="sxs-lookup"><span data-stu-id="fdc10-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="fdc10-109">Bu tür sınıflar el ile yazılmış veya komut satırı XML şemaları/veri türleri desteği yardımcı programı kullanarak XML şema türlerinin tanımlarını üretilen XSD.exe'nin.</span><span class="sxs-lookup"><span data-stu-id="fdc10-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="fdc10-110">Ne zaman .NET Framework tanımlayan sınıflar bilmeniz gereken temel sorunların bir listesini verilmiştir <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden serileştirebiliyorsa:</span><span class="sxs-lookup"><span data-stu-id="fdc10-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="fdc10-111">Yalnızca ortak alanları ve .NET Framework nesnelerin özelliklerini, XML'e çevrilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="fdc10-112">Koleksiyon sınıfları seri hale getirilemiyor XML'e sınıflar ya da uygularsanız <xref:System.Collections.IEnumerable> veya <xref:System.Collections.ICollection> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fdc10-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="fdc10-113">Uygulayan sınıflar <xref:System.Collections.IDictionary> gibi arabirim <xref:System.Collections.Hashtable>, XML'e seri hale getirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="fdc10-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="fdc10-114">Çoğu öznitelik türlerini harika <xref:System.Xml.Serialization> ad alanı, bir .NET Framework sınıf ve üyelerine sınıfının örneklerini XML içinde nasıl gösterileceğini denetlemek için eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 <span data-ttu-id="fdc10-115">WCF uygulaması geliştirme de genellikle karmaşık tür tanımı ile başlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="fdc10-116">WCF aynı .NET Framework türleri ASP.NET Web hizmetlerini kullanmak için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="fdc10-117">WCF<xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> türün örneklerinin içine XML ve hangi belirli alanlar veya tür özelliklerini seri hale getirilmesi için aşağıdaki örnek kodda gösterildiği gibi seri hale olduğunu belirtmek için .NET Framework türleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```csharp  
//Example One:   
[DataContract]  
public class LineItem  
{  
    [DataMember]  
    public string ItemNumber;  
    [DataMember]  
    public decimal Quantity;  
    [DataMember]  
    public decimal UnitPrice;  
}  
  
//Example Two:   
public class LineItem  
{  
    [DataMember]  
    private string itemNumber;  
    [DataMember]  
    private decimal quantity;  
    [DataMember]  
    private decimal unitPrice;  
  
    public string ItemNumber  
    {  
      get  
      {  
          return this.itemNumber;  
      }  
  
      set  
      {  
          this.itemNumber = value;  
      }  
    }  
  
    public decimal Quantity  
    {  
        get  
        {  
            return this.quantity;  
        }  
  
        set  
        {  
            this.quantity = value;  
        }  
    }  
  
    public decimal UnitPrice  
    {  
      get  
      {  
          return this.unitPrice;  
      }  
  
      set  
      {  
          this.unitPrice = value;  
      }  
    }  
}  
  
//Example Three:   
public class LineItem  
{  
     private string itemNumber;  
     private decimal quantity;  
     private decimal unitPrice;  
  
     [DataMember]  
     public string ItemNumber  
     {  
       get  
       {  
          return this.itemNumber;  
       }  
  
       set  
       {  
           this.itemNumber = value;  
       }  
     }  
  
     [DataMember]  
     public decimal Quantity  
     {  
          get  
          {  
              return this.quantity;  
          }  
  
          set  
          {  
             this.quantity = value;  
          }  
     }  
  
     [DataMember]  
     public decimal UnitPrice  
     {  
          get  
          {  
              return this.unitPrice;  
          }  
  
          set  
          {  
              this.unitPrice = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="fdc10-118"><xref:System.Runtime.Serialization.DataContractAttribute> Sıfır veya daha fazla türün alanlarına veya özelliklerine olması anlamına gelir serileştirildiği while <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alan veya özellik serileştirilecek olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="fdc10-119"><xref:System.Runtime.Serialization.DataContractAttribute> Bir sınıf veya yapı için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="fdc10-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Bir alan veya özellik için uygulanabilir ve alanlar ve Özellikler öznitelik uygulandığı genel veya özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="fdc10-121">Sahip türleri örneklerini <xref:System.Runtime.Serialization.DataContractAttribute> uygulanan WCF'de veri sözleşmeleri olarak bunları için başvurulur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="fdc10-122">XML olarak serileştirilme şeklini kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fdc10-123">Aşağıdakileri kullanarak arasındaki önemli farklar listesidir <xref:System.Runtime.Serialization.DataContractSerializer> ve kullanarak <xref:System.Xml.Serialization.XmlSerializer> ve çeşitli özniteliklerini <xref:System.Xml.Serialization> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fdc10-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="fdc10-124"><xref:System.Xml.Serialization.XmlSerializer> Ve özniteliklerini <xref:System.Xml.Serialization> ad alanı, XML Şeması'nda tanımlanan herhangi bir geçerli türü .NET Framework türleriyle eşlemek olanak sağlamak için tasarlanmıştır ve bu nedenle sağlamaları için bir tür XML'de nasıl temsil edildiğini üzerinde kesin denetim.</span><span class="sxs-lookup"><span data-stu-id="fdc10-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="fdc10-125"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> türü XML'de nasıl temsil edildiğini üzerinde çok az bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="fdc10-126">Yalnızca ad alanları ve tür ve alanlarını veya XML ve alanlar ve Özellikler XML dosyasında göründükleri sıra özelliklerinde temsil etmek için kullanılan adları belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdc10-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```csharp  
    [DataContract(  
    Namespace="urn:Contoso:2006:January:29",  
    Name="LineItem")]  
    public class LineItem  
    {  
         [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]  
         public string itemNumber;  
         [DataMember(Name="Quantity",IsRequired=false,Order = 1)]  
         public decimal quantity;  
         [DataMember(Name="Price",IsRequired=false,Order = 2)]  
         public decimal unitPrice;  
    }  
    ```  
  
     <span data-ttu-id="fdc10-127">.NET türü temsil etmek için kullanılan XML yapısı hakkında diğer her şey belirlenir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="fdc10-128">Nasıl bir XML içinde temsil edilmesini türüdür kadar denetim vermeyerek seri hale getirme işlemi için son derece tahmin edilebilir hale <xref:System.Runtime.Serialization.DataContractSerializer>ve böylece iyileştirmek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="fdc10-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="fdc10-129">Tasarımını pratik bir yararı <xref:System.Runtime.Serialization.DataContractSerializer> daha iyi performans, yaklaşık olarak yüzde 10 oranında daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="fdc10-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="fdc10-130">İle kullanmak için öznitelikler <xref:System.Xml.Serialization.XmlSerializer> hangi alanların veya özelliklerin türü XML serileştirilme şeklini ise göstermez <xref:System.Runtime.Serialization.DataMemberAttribute> ile kullanılmak üzere <xref:System.Runtime.Serialization.DataContractSerializer> hangi alanların veya özelliklerin serileştirilmiş açıkça gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="fdc10-131">Dolayısıyla, veri sözleşmeleri, göndermek ve almak için bir uygulama olan verilerin yapısı hakkında açık anlaşmaları altındadır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="fdc10-132"><xref:System.Xml.Serialization.XmlSerializer> Yalnızca genel üyeleri bir .NET nesnesini XML'e, çevirebilir <xref:System.Runtime.Serialization.DataContractSerializer> nesnelerin üyelerini XML'e erişim değiştiricileri bu üyelerin bağımsız olarak çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="fdc10-133">Türleri ortak olmayan üyeleri, XML'e seri hale getirmek için söz konusu kümelerdeki <xref:System.Runtime.Serialization.DataContractSerializer> daha az XML'e serileştirebiliyorsa .NET türleri çeşitli kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="fdc10-134">Özellikle, XML türlerini gibi çevirebilir <xref:System.Collections.Hashtable> uygulayan <xref:System.Collections.IDictionary> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fdc10-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="fdc10-135"><xref:System.Runtime.Serialization.DataContractSerializer> Türünün tanımını değiştirin veya bunun için bir sarmalayıcı geliştirme gerek kalmadan tüm önceden mevcut olan .NET türüne XML örneklerini serileştirmek çok daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="fdc10-136">Başka bir sonucu <xref:System.Runtime.Serialization.DataContractSerializer> bir türün genel olmayan üyeleri erişebildiklerinden olan tam güven gerektirir ancak <xref:System.Xml.Serialization.XmlSerializer> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fdc10-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="fdc10-137">Tam güven kodu erişim izni altında kodu yürüten kimlik bilgileri kullanılarak erişilebilecek bir makinedeki tüm kaynakların tam erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="fdc10-138">Tam olarak güvenilen kod makinenizde tüm kaynaklara erişir gibi bu seçeneği dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="fdc10-139"><xref:System.Runtime.Serialization.DataContractSerializer> Bazı sürüm oluşturma desteği içerir:</span><span class="sxs-lookup"><span data-stu-id="fdc10-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="fdc10-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> böylece uygulamaların olmasını sözleşmenin daha yeni sürümü izin verecek şekilde önceki sürümlerde, mevcut olmayan bir veri anlaşması yeni sürümlerine eklenen üyeler için false değeri atanabilir özelliği önceki sürümlerde işlemek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdc10-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="fdc10-141">Uygulama bir veri anlaşması sahip <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi, bir izin verebilir <xref:System.Runtime.Serialization.DataContractSerializer> uygulamalar üzerinden bir veri anlaşması daha yeni sürümlerinde sözleşme önceki sürümleriyle tanımlanan üyeler geçirilecek.</span><span class="sxs-lookup"><span data-stu-id="fdc10-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="fdc10-142">Tüm farklılıklar da XML'e rağmen <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlamı da XML'e aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir türü seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="fdc10-143">Anlamsal olarak aynı XML tarafından öznitelikleri hem seri hale getiricileri genişletme ile kullanmak için aşağıdaki sınıf çevrilir <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="fdc10-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]  
[DataContract(Namespace="urn:Contoso:2006:January:29")]  
public class LineItem  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
```  
  
 <span data-ttu-id="fdc10-144">Windows Yazılım Geliştirme Seti (SDK) adlı bir komut satırı aracı içerir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fdc10-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="fdc10-145">ASP.NET Web Hizmetleri ile kullanılan XSD.exe'nin aracını gibi Svcutil.exe XML şema .NET veri türlerinin tanımlarını oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="fdc10-146">Veri sözleşmeleri, türleridir <xref:System.Runtime.Serialization.DataContractSerializer> XML XML şeması tarafından tanımlanan biçimde gönderebilir; Aksi takdirde, bunlar serileştirme kullanmak için tasarlanmıştır <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fdc10-147">Svcutil.exe ayrıca oluşturabileceği bir XML Şeması veri sözleşmelerden kullanarak kendi `dataContractOnly` geçin.</span><span class="sxs-lookup"><span data-stu-id="fdc10-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdc10-148">ASP.NET Web hizmetlerini kullanın ancak <xref:System.Xml.Serialization.XmlSerializer>ve WCF ASP.NET uyumluluk modunun ASP.NET Web hizmetlerini davranışını taklit eden WCF hizmetleri sağlar, ASP.NET uyumluluk seçeneğini kullanarak bir kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fdc10-149">Bir kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetleri ile.</span><span class="sxs-lookup"><span data-stu-id="fdc10-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="fdc10-150">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="fdc10-150">Service Development</span></span>  
 <span data-ttu-id="fdc10-151">ASP.NET kullanarak bir hizmeti geliştirmek için eklemek için her zamanki geçtiğine <xref:System.Web.Services.WebService> öznitelik bir sınıfa ve <xref:System.Web.Services.WebMethodAttribute> herhangi bir hizmet işlemlerini olacak bu sınıfı yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="fdc10-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```csharp  
[WebService]  
public class Service : T:System.Web.Services.WebService  
{  
    [WebMethod]  
    public string Echo(string input)   
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="fdc10-152">ASP.NET 2.0 kullanılmaya öznitelik ekleme seçeneğiniz <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> bir arabirim yerine bir sınıf ve arabirim uygulamak için bir sınıf yazma:</span><span class="sxs-lookup"><span data-stu-id="fdc10-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```csharp  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="fdc10-153">Bu seçeneği kullanarak, tercih edilen, olmasını çünkü arabirimiyle <xref:System.Web.Services.WebService> özniteliği aynı sözleşme farklı şekillerde uygulayabilir, çeşitli sınıflarla yeniden kullanılabilir bir hizmet tarafından gerçekleştirilen işlemleri için bir sözleşmeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="fdc10-154">Bir WCF hizmeti bir veya daha fazla WCF bitiş noktalarını tanımlayarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="fdc10-155">Bir uç nokta bir adresi, bağlama ve hizmet sözleşmesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="fdc10-156">Hizmet bulunduğu adresin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-156">The address defines where the service is located.</span></span> <span data-ttu-id="fdc10-157">Bağlama hizmeti ile iletişim kurma belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="fdc10-158">Hizmet sözleşmesi, hizmet gerçekleştirebileceği işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-158">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="fdc10-159">Hizmet sözleşmesi genellikle ilk olarak ekleyerek tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> bir arabirim için:</span><span class="sxs-lookup"><span data-stu-id="fdc10-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```csharp  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="fdc10-160"><xref:System.ServiceModel.ServiceContractAttribute> Arabirimi bir WCF hizmet sözleşmesini tanımlayan belirtir ve <xref:System.ServiceModel.OperationContractAttribute> , varsa, arabirimin yöntemlerini hizmet sözleşmesi işlemlerini tanımlayan gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="fdc10-161">Bir hizmet sözleşmesini tanımlandıktan sonra hizmet sözleşmesi tanımlandığı arabirimini uygulayan sınıf sağlayarak bir sınıfta uygulanır:</span><span class="sxs-lookup"><span data-stu-id="fdc10-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```csharp  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="fdc10-162">Bir hizmet sözleşmesini uygulayan bir sınıf, bir hizmet olarak WCF'de türüne adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>  
  
 <span data-ttu-id="fdc10-163">Sonraki adım, bir adresi ve bir bağlama bir hizmet türü ile ilişkilendirin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="fdc10-164">Bu, genellikle bir yapılandırma dosyasında, dosyanın doğrudan düzenleyerek veya WCF ile sağlanan bir yapılandırma Düzenleyicisi'ni kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="fdc10-165">Bir yapılandırma dosyası örneği aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-165">Here is an example of a configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
     <system.serviceModel>  
      <services>  
      <service name="Service ">  
       <endpoint   
        address="EchoService"  
        binding="basicHttpBinding"  
        contract="IEchoService "/>  
      </service>  
      </services>  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fdc10-166">Bağlama uygulamayla iletişim protokolleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="fdc10-167">Aşağıdaki tabloda, sık kullanılan seçenekleri temsil eden sistem tarafından sağlanan bağlamalar listeler.</span><span class="sxs-lookup"><span data-stu-id="fdc10-167">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="fdc10-168">Ad</span><span class="sxs-lookup"><span data-stu-id="fdc10-168">Name</span></span>|<span data-ttu-id="fdc10-169">Amaç</span><span class="sxs-lookup"><span data-stu-id="fdc10-169">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="fdc10-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-170">BasicHttpBinding</span></span>|<span data-ttu-id="fdc10-171">Web Hizmetleri ve temel güvenlik profili 1.0 ve 1.1 WS-BasicProfile destekleyen istemciler ile birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="fdc10-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="fdc10-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-172">WSHttpBinding</span></span>|<span data-ttu-id="fdc10-173">Web Hizmetleri ve desteği WS - istemcileri ile birlikte çalışabilirlik \* protokolleri HTTP üzerinden.</span><span class="sxs-lookup"><span data-stu-id="fdc10-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|  
|<span data-ttu-id="fdc10-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-174">WSDualHttpBinding</span></span>|<span data-ttu-id="fdc10-175">Çift yönlü HTTP iletişimi, bir ilk ileti alıcısı doğrudan ilk göndereni yanıtlamak değil, ancak yanıt herhangi bir sayıda in conformity with WS - HTTP kullanarak bir süre iletebilen \* protokoller.</span><span class="sxs-lookup"><span data-stu-id="fdc10-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|  
|<span data-ttu-id="fdc10-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-176">WSFederationBinding</span></span>|<span data-ttu-id="fdc10-177">Bir hizmeti kaynaklarına erişimi denetlenebilir, HTTP iletişimi bir açıkça tanımlanmış kimlik bilgisi sağlayıcısı tarafından verilen kimlik bilgilerini temel.</span><span class="sxs-lookup"><span data-stu-id="fdc10-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="fdc10-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-178">NetTcpBinding</span></span>|<span data-ttu-id="fdc10-179">Bir ağ üzerinden WCF yazılım varlıklar arasında güvenli, güvenilir ve yüksek performanslı iletişim.</span><span class="sxs-lookup"><span data-stu-id="fdc10-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|  
|<span data-ttu-id="fdc10-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="fdc10-181">WCF yazılım varlıkları aynı makinede arasındaki iletişimi güvenli, güvenilir ve yüksek performans.</span><span class="sxs-lookup"><span data-stu-id="fdc10-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|  
|<span data-ttu-id="fdc10-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-182">NetMsmqBinding</span></span>|<span data-ttu-id="fdc10-183">MSMQ kullanarak WCF yazılım varlıklar arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="fdc10-183">Communication between WCF software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="fdc10-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="fdc10-185">Bir WCF yazılım varlık ve MSMQ kullanarak başka bir yazılım varlığı arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="fdc10-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="fdc10-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="fdc10-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="fdc10-187">Windows Eşler arası ağ iletişimi kullanarak WCF yazılım varlıklar arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="fdc10-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="fdc10-188">Sistem tarafından sağlanan bağlama <xref:System.ServiceModel.BasicHttpBinding>, ASP.NET Web Hizmetleri tarafından desteklenen protokolleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="fdc10-189">Özel bağlamalar WCF uygulamaları için kolayca bağlama öğesi sınıflarının tekil protokollerin uygulamak için WCF kullanan bir koleksiyon olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="fdc10-190">Ek protokollerin temsil etmek için yeni bağlama öğeleri yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-190">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="fdc10-191">Hizmet türlerini iç davranışını davranışları adlı sınıflar ailesini özelliklerini kullanarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="fdc10-192">Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıfı hizmet türü birden çok iş parçacıklı değer olduğunu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```csharp  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="fdc10-193">Bazı davranışları ister <xref:System.ServiceModel.ServiceBehaviorAttribute>, öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="fdc10-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="fdc10-194">Diğer yöneticiler ayarlamak için isteyeceği özelliklere sahip olanları uygulama yapılandırmasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="fdc10-195">Hizmet türlerini programlamada, sık kullanılan oluşuyor <xref:System.ServiceModel.OperationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fdc10-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="fdc10-196">Kendi statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği işleminin çalıştığı bağlamı bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="fdc10-197"><xref:System.ServiceModel.OperationContext> her ikisi için de benzer <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="fdc10-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="fdc10-198">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fdc10-198">Hosting</span></span>  
 <span data-ttu-id="fdc10-199">ASP.NET Web Hizmetleri, bir sınıf kitaplık derlemesine derlenir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="fdc10-200">Hizmet dosyası adlı bir dosya uzantısı .asmx sahip ve içeren koşuluyla olan bir `@ WebService` hizmet ve onu bulunduğu bütünleştirilmiş kod için kod içeren sınıf tanımlayan yönergesi.</span><span class="sxs-lookup"><span data-stu-id="fdc10-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="fdc10-201">Internet Information Services (IIS) ASP.NET uygulama kökü hizmet dosyası kopyalanır ve derleme, uygulama kök \bin alt kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="fdc10-202">Uygulama ardından Tekdüzen Kaynak Konum Belirleyicisi (URL) ' hizmet dosyasının uygulama kökü kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 <span data-ttu-id="fdc10-203">WCF hizmetlerinde IIS 5.1 veya 6.0, Windows İşlem Etkinleştirme Hizmeti (IIS 7. 0'da, bir parçası olarak sağlanan WAS) ve herhangi bir .NET uygulama içinde kolayca barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="fdc10-204">IIS 5.1 veya 6.0 hizmet barındırmak için hizmet iletişimleri Aktarım Protokolü olarak HTTP kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="fdc10-205">IIS 5.1, 6.0 veya WAS içinde bir hizmet ana bilgisayar için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="fdc10-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="fdc10-206">Hizmet türü bir sınıf kitaplık derlemesine içine derleyin.</span><span class="sxs-lookup"><span data-stu-id="fdc10-206">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="fdc10-207">.Svc uzantısına sahip bir hizmet dosyası oluşturma bir `@ ServiceHost` yönergesi hizmet türünü tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="fdc10-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="fdc10-208">Bir sanal dizin ve bu sanal dizine \bin alt derlemeye hizmet dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fdc10-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="fdc10-209">Yapılandırma dosyasını sanal dizine kopyalayın ve bunu Web.config olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="fdc10-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="fdc10-210">Uygulama daha sonra uygulama kökü hizmet dosyasında URL'si kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-210">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="fdc10-211">Bir .NET uygulamasından bir WCF Hizmeti barındırma için hizmet türü uygulama tarafından başvurulan bir sınıf kitaplık derlemesine derlemek ve konak hizmetini kullanarak uygulamayı programlama <xref:System.ServiceModel.ServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fdc10-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="fdc10-212">Gerekli temel programlama örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fdc10-212">The following is an example of the basic programming required:</span></span>  
  
```csharp  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="fdc10-213">Bu örnek, bir veya daha fazla aktarım protokolleri için adresleri oluşumunu nasıl belirtilen gösterir. bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="fdc10-214">Bu adresler taban adresi adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-214">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="fdc10-215">Herhangi bir WCF Hizmeti uç noktası için sağlanan adresi, temel bir uç noktanın ana bilgisayar adresini göre adresidir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="fdc10-216">Konak her iletişim Aktarım Protokolü için bir temel adresine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="fdc10-217">Önceki yapılandırma dosyasında örnek yapılandırmasında <xref:System.ServiceModel.BasicHttpBinding> HTTP uç noktası kullanımıyla ilgili Aktarım Protokolü bu nedenle, uç nokta adresini seçili `EchoService`, ana bilgisayarın HTTP temel adresi göre.</span><span class="sxs-lookup"><span data-stu-id="fdc10-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="fdc10-218">Önceki örnekte konağın söz konusu olduğunda, HTTP temel adresi olduğundan `http://www.contoso.com:8000/`.</span><span class="sxs-lookup"><span data-stu-id="fdc10-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="fdc10-219">IIS veya WAS içinde barındırılan bir hizmet için taban adresi hizmetin hizmet dosyası URL'sidir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="fdc10-220">Yalnızca hizmetler IIS veya WAS ve hangi HTTP ile Aktarım Protokolü yalnızca, yapılandırılmış barındırılan WCF ASP.NET uyumluluk modu seçeneğini kullanmak için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="fdc10-221">Bu seçeneği etkinleştirmek için aşağıdaki adımları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-221">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="fdc10-222">Programcı eklemelisiniz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> özniteliği için hizmet türü ve ASP.NET uyumluluk modunun izin verilen veya gerekli belirtin.</span><span class="sxs-lookup"><span data-stu-id="fdc10-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```csharp  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="fdc10-223">Yönetici, ASP.NET uyumluluk modunun kullanmak için uygulamayı yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
    ```xml  
    <configuration>  
         <system.serviceModel>  
          <services>  
          […]  
          </services>  
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="fdc10-224">WCF uygulamaları, kendi hizmet dosyalarda .svc yerine .asmx bir uzantısı olarak kullanmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="fdc10-225">Bu seçenek, WCF kullanmak için hizmet değiştirilirken .asmx hizmeti dosyaları URL'lerini kullanmak üzere yapılandırılmış istemciler değiştirmek zorunda kalmaktan kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdc10-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="fdc10-226">İstemci geliştirme</span><span class="sxs-lookup"><span data-stu-id="fdc10-226">Client Development</span></span>  
 <span data-ttu-id="fdc10-227">ASP.NET Web Hizmetleri için istemcileri, giriş olarak .asmx dosyasının URL'sini sağlayan WSDL.exe komut satırı aracını kullanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="fdc10-228">WCF tarafından sağlanan karşılık gelen aracı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fdc10-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="fdc10-229">Bu, bir kod modülü ile hizmet sözleşmesi tanımını ve bir WCF istemcisi sınıfının tanımını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="fdc10-230">Ayrıca, hizmetin bağlamasını ve adresini içeren bir yapılandırma dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-230">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="fdc10-231">Uzak bir hizmete istemcisini programlamada zaman uyumsuz bir modele göre program genellikle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="fdc10-232">Her zaman WSDL.exe araç tarafından oluşturulan kodu, bir zaman uyumlu hem de zaman uyumsuz bir desenin için varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="fdc10-233">Tarafından oluşturulan kodu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) için ya da bir desen girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdc10-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="fdc10-234">Bu, varsayılan olarak zaman uyumlu desenini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="fdc10-235">Aracı ile yürütülürse `/async` geçiş için zaman uyumsuz desen oluşturulan kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="fdc10-236">ASP tarafından oluşturulan WCF istemci sınıfları adları bir garanti yoktur. Varsayılan olarak, NET WSDL.exe aracı Svcutil.exe araç tarafından oluşturulan WCF istemci sınıfları adlarında eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="fdc10-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="fdc10-237">Özellikle, özelliklerin sınıflarının adları olan kullanarak serileştirilecek <xref:System.Xml.Serialization.XmlSerializer> WSDL.exe aracı ile çalışması değil Svcutil.exe aracı tarafından oluşturulan kodu soneki özelliği varsayılan olarak, verilen olan.</span><span class="sxs-lookup"><span data-stu-id="fdc10-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="fdc10-238">İleti gösterimi</span><span class="sxs-lookup"><span data-stu-id="fdc10-238">Message Representation</span></span>  
 <span data-ttu-id="fdc10-239">ASP.NET Web Hizmetleri tarafından alınan SOAP iletilerinin üstbilgisi özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="fdc10-240">Öğesinden türetilen bir sınıf <xref:System.Web.Services.Protocols.SoapHeader> başlık yapısını tanımlamak için ve ardından <xref:System.Web.Services.Protocols.SoapHeaderAttribute> üst bilgisi varlığını göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```csharp  
public class SomeProtocol : SoapHeader  
{  
     public long CurrentValue;  
     public long Total;  
}  
  
[WebService]  
public interface IEcho  
{  
     SomeProtocol ProtocolHeader  
     {  
      get;  
     set;  
     }  
  
     [WebMethod]  
     [SoapHeader("ProtocolHeader")]  
     string PlaceOrders(PurchaseOrderType order);  
}  
  
public class Service: WebService, IEcho  
{  
     private SomeProtocol protocolHeader;  
  
     public SomeProtocol ProtocolHeader  
     {  
         get  
         {  
              return this.protocolHeader;  
         }  
  
         set  
         {  
              this.protocolHeader = value;  
         }  
     }  
  
     string PlaceOrders(PurchaseOrderType order)  
     {  
         long currentValue = this.protocolHeader.CurrentValue;  
     }  
}  
```  
  
 <span data-ttu-id="fdc10-241">WCF öznitelikleri sağlar <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ve <xref:System.ServiceModel.MessageBodyMemberAttribute> SOAP iletilerini bir hizmeti tarafından gönderilen ve alınan yapısını tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="fdc10-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```csharp  
[DataContract]  
public class SomeProtocol  
{  
     [DataMember]  
     public long CurrentValue;  
     [DataMember]  
     public long Total;  
}  
  
[DataContract]  
public class Item  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
  
[MessageContract]  
public class ItemMesage  
{  
     [MessageHeader]  
     public SomeProtocol ProtocolHeader;  
     [MessageBody]  
     public Item Content;  
}  
  
[ServiceContract]  
public interface IItemService  
{  
     [OperationContract]  
     public void DeliverItem(ItemMessage itemMessage);  
}  
```  
  
 <span data-ttu-id="fdc10-242">İletileri yapısı, bir ASP.NET Web hizmeti kodunu tarafından kapsanan ise bu söz dizimi yapısı iletileri, açık bir temsilini verir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="fdc10-243">Ayrıca, ASP.NET sözdiziminde, ileti üstbilgileri hizmet özellikleri olarak gibi gösterilir `ProtocolHeader` önceki örnekte, özellik daha doğru bir şekilde iletileri özellikleri olarak gösterilen WCF sözdiziminde ise.</span><span class="sxs-lookup"><span data-stu-id="fdc10-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="fdc10-244">Ayrıca, WCF uç noktaları yapılandırmanız için eklenecek ileti üstbilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>  
  
```xml  
<service name="Service ">  
     <endpoint   
      address="EchoService"  
      binding="basicHttpBinding"  
      contract="IEchoService ">  
      <headers>  
      <dsig:X509Certificate   
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">  
       ...  
      </dsig:X509Certificate>  
      </headers>  
     </endpoint>  
</service>  
```  
  
 <span data-ttu-id="fdc10-245">Seçenek, herhangi bir istemci veya hizmet için kodunda altyapısal protokol üstbilgileri başvuru kaçınmak olanak tanır: uç nokta nasıl yapılandırıldığını nedeniyle ileti üstbilgileri eklenir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="fdc10-246">Hizmet Açıklaması</span><span class="sxs-lookup"><span data-stu-id="fdc10-246">Service Description</span></span>  
 <span data-ttu-id="fdc10-247">WSDL sorgu ile bir ASP.NET Web hizmetinin .asmx dosyası için bir HTTP GET isteği verme, WSDL hizmet oluşturmak ASP.NET neden olur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="fdc10-248">Bunu döndüren WSDL isteğe yanıt olarak.</span><span class="sxs-lookup"><span data-stu-id="fdc10-248">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="fdc10-249">ASP.NET 2.0 yapılan bu hizmet Web Hizmetleri birlikte çalışabilirlik kuruluşun Basic Profile 1.1 ile uyumlu olduğunu doğrulamak olası (WS-ı) ve hizmet içinde WSDL uyumlu bir talep eklemek için.</span><span class="sxs-lookup"><span data-stu-id="fdc10-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="fdc10-250">Diğer bir deyişle bitti kullanarak `ConformsTo` ve `EmitConformanceClaims` parametrelerinin <xref:System.Web.Services.WebServiceBindingAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fdc10-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="fdc10-251">ASP.NET, bir hizmet için üretir. WSDL özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="fdc10-252">Özelleştirmeleri, türetilmiş sınıf oluşturarak yapılır <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> için WSDL öğeleri eklemek için.</span><span class="sxs-lookup"><span data-stu-id="fdc10-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="fdc10-253">IIS 51 içinde barındırılan bir HTTP uç noktası ile ' % s'sorgu WSDL .svc dosyasının bir WCF Hizmeti ile bir HTTP GET isteği verme, 6.0 veya WAS'ta WCF hizmet WSDL ile yanıt neden olur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="fdc10-254">Bir .NET uygulamasında barındırılan bir hizmete HTTP temel adresine WSDL sorgu ile bir HTTP GET isteği veren aynı etkiye sahiptir de ayarlanmışsa true.</span><span class="sxs-lookup"><span data-stu-id="fdc10-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="fdc10-255">Ancak, WCF Ayrıca, bir hizmet oluşturduğu WSDL WS-MetadataExchange isteklerine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="fdc10-256">ASP.NET Web hizmetlerini WS-MetadataExchange istekleri için yerleşik destek yok.</span><span class="sxs-lookup"><span data-stu-id="fdc10-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="fdc10-257">WCF oluşturur WSDL kapsamlı olarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="fdc10-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfı WSDL özelleştirmeye yönelik bazı özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="fdc10-259">WCF WSDL oluşturulmayacağını, ancak bunun yerine belirtilen URL'de statik bir WSDL dosyasını kullanmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DescriptionBehavior">  
     <metadataPublishing   
      enableMetadataExchange="true"   
      enableGetWsdl="true"   
      enableHelpPage="true"   
      metadataLocation=  
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>  
     </behavior>  
</behaviors>  
```  
  
## <a name="exception-handling"></a><span data-ttu-id="fdc10-260">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="fdc10-260">Exception Handling</span></span>  
 <span data-ttu-id="fdc10-261">ASP.NET Web Hizmetleri, işlenmemiş özel durumlar, SOAP hataları istemcilere döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fdc10-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="fdc10-262">Örneklerini de açıkça oluşturabilecek <xref:System.Web.Services.Protocols.SoapException> sınıfı ve istemciye gönderilen bir SOAP hatası içeriği hakkında daha fazla denetime sahip.</span><span class="sxs-lookup"><span data-stu-id="fdc10-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="fdc10-263">WCF hizmetleri, işlenmemiş özel durumlar istemcilere hassas bilgiler özel durumların yanlışlıkla yararlanılmasını önlemek için SOAP hataları olarak döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="fdc10-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="fdc10-264">Bir yapılandırma ayarı, hata ayıklama amacıyla, istemcilere döndürülen özel durum işlenmemiş için sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="fdc10-265">SOAP hataları istemcilere dönmek için genel türün örneklerini oluşturabilecek <xref:System.ServiceModel.FaultException%601>kullanarak veri anlaşması türü olarak genel tür.</span><span class="sxs-lookup"><span data-stu-id="fdc10-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="fdc10-266">Ayrıca ekleyebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> öznitelikleri, işlemleri bir işlem yield hataları belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="fdc10-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```csharp  
[DataContract]  
public class MathFault  
{   
     [DataMember]  
     public string operation;  
     [DataMember]  
     public string problemType;  
}  
  
[ServiceContract]  
public interface ICalculator  
{  
     [OperationContract]  
     [FaultContract(typeof(MathFault))]  
     int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="fdc10-267">Olası hataları sonuçlarında hizmeti için WSDL içinde tanıtılan şekilde yaptığını, hangi hataların öngörmek programcılar rotasyonunun bir işlemden neden ve uygun catch deyimleri yazma.</span><span class="sxs-lookup"><span data-stu-id="fdc10-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```csharp  
try  
{  
     result = client.Divide(value1, value2);  
}  
catch (FaultException<MathFault> e)  
{  
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "  
  + e.Detail.operation   
  + ". Problem: "   
  + e.Detail.problemType);  
}  
```  
  
## <a name="state-management"></a><span data-ttu-id="fdc10-268">Durum Yönetimi</span><span class="sxs-lookup"><span data-stu-id="fdc10-268">State Management</span></span>  
 <span data-ttu-id="fdc10-269">Bir ASP.NET Web hizmeti uygulamak için kullanılan sınıfı türetilen <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```csharp  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="fdc10-270">Bu durumda, sınıf kullanılacak programlanabilir <xref:System.Web.Services.WebService> erişmek için sınıfın bağlam özelliğini temel bir <xref:System.Web.HttpContext> nesne.</span><span class="sxs-lookup"><span data-stu-id="fdc10-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="fdc10-271"><xref:System.Web.HttpContext> Nesnesi olabilir güncelleştirme ve kendi uygulama özelliğini kullanarak uygulama durum bilgilerini almak için kullanılan ve güncelleştirme ve kendi oturumu özelliğini kullanarak oturum durumu bilgilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="fdc10-272">ASP.NET, burada oturum durum bilgileri oturumu özelliği kullanılarak önemli ölçüde denetim sağlar <xref:System.Web.HttpContext> gerçekten depolanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="fdc10-273">Tanımlama bilgileri, bir veritabanı, geçerli sunucu belleği veya atanmış bir sunucu belleği depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="fdc10-274">Seçim hizmet yapılandırma dosyasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-274">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="fdc10-275">WCF genişletilebilen nesneler için durum yönetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="fdc10-276">Genişletilebilen nesneler olan uygulayan nesneler <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="fdc10-277">En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="fdc10-278">`ServiceHostBase` tüm hizmet örneklerinin türleri, aynı ana bilgisayarda durumu erişebilir, tutmanıza olanak sağlayan while `InstanceContext` içinde bir hizmet türünün aynı örneğini çalıştıran herhangi bir kod tarafından erişilebilir durumda tutmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="fdc10-279">Burada, hizmet türü `TradingSystem`, sahip bir <xref:System.ServiceModel.ServiceBehaviorAttribute> belirten tüm çağrıların aynı WCF istemci örneğinin aynı hizmet türü örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>  
  
```csharp  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="fdc10-280">Sınıf `DealData`, bir hizmet türünün aynı örneğinde çalışan herhangi bir kod tarafından erişilebilecek bir durum tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```csharp  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="fdc10-281">Hizmet türünün hizmet sözleşmesinin işlemlerden uygulayan kod bir `DealData` durum nesnesi, geçerli hizmet türü örneği durumuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```csharp  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="fdc10-282">Bu durum nesnesi alınır ve başka bir hizmet sözleşme işlemleri uygulayan kodu tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="fdc10-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```csharp  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="fdc10-283">ASP.NET üzerinde denetim sağlar. burada bilgileri durum <xref:System.Web.HttpContext> sınıfı gerçekten depolanan, WCF, en az ilk sürümde genişletilebilen nesneler depolandığı üzerinde hiçbir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="fdc10-284">Bir WCF hizmeti için ASP.NET uyumluluk modunun seçmeye yönelik en iyi nedeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="fdc10-285">Yapılandırılabilir durum yönetimi, kesinlik temelli sonra için ASP.NET uyumluluk modunun edilmesiyle akreditasyonlu kullanmanıza olanak verir <xref:System.Web.HttpContext> sınıf tam olarak, ASP.NET ve yapılandırmak için kullanılabilir olduğu durum kullanılarakyönetilenbilgileri<xref:System.Web.HttpContext> sınıfı depolanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="fdc10-286">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="fdc10-286">Security</span></span>  
 <span data-ttu-id="fdc10-287">ASP.NET Web hizmetlerinin güvenliğini sağlamak için seçenekleri herhangi bir IIS uygulama güvenliğini sağlamak için olanlardır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="fdc10-288">WCF uygulamaları barındırılabilir, yalnızca IIS içinde aynı zamanda herhangi bir .NET yürütülebilir dosya içinde olduğundan, WCF uygulamalarının güvenliğini sağlama seçenekleri IIS akreditasyonlu bağımsız olarak yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="fdc10-289">Ancak, ASP.NET Web Hizmetleri için sağlanan özellikleri de ASP.NET uyumluluk modunda çalışan WCF hizmetleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="fdc10-290">Güvenlik: Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="fdc10-290">Security: Authentication</span></span>  
 <span data-ttu-id="fdc10-291">IIS tarafından anonim erişim veya kimlik doğrulama modları çeşitli seçebilirsiniz uygulamalara erişimi denetlemek için olanakları sağlar: Windows kimlik doğrulamasını, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="fdc10-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="fdc10-292">ASP.NET Web hizmetlerini erişimi denetlemek için Windows kimlik doğrulaması seçeneği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="fdc10-293">Ancak, WCF uygulamaları IIS içinde barındırıldığında, söz konusu kimlik doğrulamasını çeşitli seçenekler arasında Windows kimlik doğrulamasını destekleyen WCF kendisi tarafından yönetilebilmesi için uygulama anonim erişime izin vermek için IIS yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="fdc10-294">Kullanıcı adı belirteçleri, X.509 sertifikaları, SAML belirteçlerini ve CardSpace kart yerleşik diğer seçenekleri içerir, ancak özel kimlik doğrulama mekanizmaları da tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="fdc10-295">Güvenlik: Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="fdc10-295">Security: Impersonation</span></span>  
 <span data-ttu-id="fdc10-296">ASP.NET, ASP.NET Web hizmeti, belirli bir kullanıcının kimliğine bürünmesine yapılabilir veya hangi kullanıcının kimlik bilgilerinin geçerli istekle birlikte sağlanan bir kimlik öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="fdc10-297">Bu öğe, kimliğe bürünme ASP.NET uyumluluk modunda çalışan WCF uygulamaları yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="fdc10-298">WCF yapılandırma sistemi, belirli bir kullanıcının kimliğine bürünmek üzere atamak için kendi kimlik öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="fdc10-299">Ayrıca, WCF istemciler ve hizmetler bağımsız olarak kimliğe bürünme için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="fdc10-300">İstemci isteklerini iletebileceği, geçerli kullanıcının kimliğine bürünmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="fdc10-301">Hizmet işlemleri, hangi kullanıcının kimlik bilgilerinin geçerli istekle birlikte sağlanan kimliğine bürünmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```csharp  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="fdc10-302">Güvenlik: Yetkilendirme, erişim denetim listeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="fdc10-302">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="fdc10-303">Erişim denetim listeleri (ACL'ler) .asmx dosyalara erişimi kısıtlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="fdc10-304">Ancak, WCF .svc dosyalarını ACL'lerin dışında ASP.NET uyumluluk modunda yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="fdc10-305">Güvenlik: Rol tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="fdc10-305">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="fdc10-306">IIS Windows kimlik doğrulaması seçeneği birlikte ASP.NET yapılandırma dil tarafından sağlanan yetkilendirme öğesi ile kullanıcılara atanmış olan Windows gruplarını temel alan bir ASP.NET Web Hizmetleri için rol tabanlı yetkilendirme kolaylaştırmak için kullanılabilir .</span><span class="sxs-lookup"><span data-stu-id="fdc10-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="fdc10-307">ASP.NET 2.0 kullanılmaya daha genel bir rol tabanlı yetkilendirme mekanizması: rol sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="fdc10-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="fdc10-308">Rol sağlayıcıları tamamı enquiring kendisine atanmış bir kullanıcı rolleri hakkında temel bir arabirim uygular, ancak her rol sağlayıcısını farklı bir kaynaktan bu bilgileri almak nasıl bilir sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="fdc10-309">ASP.NET 2.0, rol atamaları, Windows Server 2003 Yetkilendirme Yöneticisi'nden alabileceğiniz bir Microsoft SQL Server veritabanı ve başka bir rol atamaları alabileceğiniz bir rol sağlayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="fdc10-310">Rol sağlayıcı mekanizması gerçekten WCF uygulaması da dahil olmak üzere bir .NET uygulamasında ASP.NET bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="fdc10-311">WCF uygulaması için aşağıdaki örnek yapılandırma nasıl bir ASP.NET rol sağlayıcıyı kullanımı yoluyla bir seçeneğe gösterilir <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
     <services>  
         <service name="Service.ResourceAccessServiceType"   
             behaviorConfiguration="ServiceBehavior">  
             <endpoint   
              address="ResourceAccessService"   
              binding="wsHttpBinding"   
              contract="Service.IResourceAccessContract"/>  
         </service>  
     </services>  
     <behaviors>  
       <behavior name="ServiceBehavior">  
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>  
      </behavior>  
     </behaviors>  
</system.serviceModel>  
```  
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="fdc10-312">Güvenlik: Beyana Dayalı Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="fdc10-312">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="fdc10-313">WCF en önemli yeniliklerden taleplere göre korumalı kaynaklara erişimi yetkilendirmek için kapsamlı desteklemesidir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="fdc10-314">Talep türü, bir hak ve bir değer, bir sürücü lisans, örneğin oluşur.</span><span class="sxs-lookup"><span data-stu-id="fdc10-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="fdc10-315">Doğum tarihi taşıyıcı'nın biri olan taşıyıcı hakkında talepler kümesi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="fdc10-316">Talep değeri sürücünün doğum tarihi olsa da bu talebi doğum tarihi, türüdür.</span><span class="sxs-lookup"><span data-stu-id="fdc10-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="fdc10-317">Bir talep üzerinde taşıyıcı confers sağ taşıyıcı talebin değer ile neler yapabileceğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="fdc10-318">Doğum tarihi sürücünün talep söz konusu olduğunda, sağ mülkü olduğundan: sürücü doğum tarihi ancak, örneğin yükleyemediği sahip, üzerinde değişiklik.</span><span class="sxs-lookup"><span data-stu-id="fdc10-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="fdc10-319">Beyana dayalı yetkilendirme, rol talep türü olduğundan rol tabanlı yetkilendirme barındırır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="fdc10-320">Taleplere göre yetkilendirme Karşılaştırma işleminin ve bu karşılaştırma sonucunu bağlı olarak erişim gereksinimlerini için talepler kümesi vererek ya da işlemi erişimi reddetmeden gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="fdc10-321">WCF'de, beyana dayalı yetkilendirme, bir değere atayarak yeniden çalıştırmak için kullanılacak bir sınıf belirtebilirsiniz `ServiceAuthorizationManager` özelliği <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fdc10-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="fdc10-322">Beyana dayalı yetkilendirme çalıştırmak için kullanılan sınıfların türetilmesi gereken <xref:System.ServiceModel.ServiceAuthorizationManager>, geçersiz kılmak için yalnızca bir yöntem olan `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="fdc10-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="fdc10-323">WCF hizmeti bir işlem çağrılır ve sağlar, yöntemini çağırır bir <xref:System.ServiceModel.OperationContext> kullanıcı için talepleri olan bir nesne içinde kendi `ServiceSecurityContext.AuthorizationContext` özelliği.</span><span class="sxs-lookup"><span data-stu-id="fdc10-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="fdc10-324">WCF çalışır, hangi güvenlik belirteci kullanıcı hakkında talepleri derleyerek bırakan kimlik doğrulaması için belirtilen kullanıcı bu talepleri söz konusu işlem için yeterli olup olmadığını değerlendirmek, görev.</span><span class="sxs-lookup"><span data-stu-id="fdc10-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="fdc10-325">Kimlik doğrulama mekanizması tamamen bağımsız taleplere göre yetkilendirme kodunu kolaylaştırır WCF güvenlik herhangi bir türden otomatik olarak talep çeviren son derece önemli bir yenilik belirteci olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="fdc10-326">Aksine, ASP.NET'te ACL'leri ya da rolleri kullanarak yetkilendirme için Windows kimlik doğrulaması yakından bağlanır.</span><span class="sxs-lookup"><span data-stu-id="fdc10-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="fdc10-327">Güvenlik: Gizliliği</span><span class="sxs-lookup"><span data-stu-id="fdc10-327">Security: Confidentiality</span></span>  
 <span data-ttu-id="fdc10-328">ASP.NET Web Hizmetleri ile değiştirilen iletilerin gizliliğini taşıma düzeyinde IIS içinde uygulamayı Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak güvence altına alınabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="fdc10-329">Aynı içinde IIS barındırılan WCF uygulamaları için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="fdc10-330">Ancak, dışında IIS barındırılan WCF uygulamaları güvenli aktarım protokolünü kullanmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="fdc10-331">Daha da önemlisi, WCF uygulamaları, bunlar, WS-güvenlik protokolü kullanarak taşınacağını önce iletileri güvenli hale getirmek için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="fdc10-332">WS-güvenlik kullanarak ileti gövdesi güvenli hale getirme aracılar son hedefine ulaşmadan önce ilkemiz aktarılan izin verir.</span><span class="sxs-lookup"><span data-stu-id="fdc10-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="fdc10-333">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="fdc10-333">Globalization</span></span>  
 <span data-ttu-id="fdc10-334">ASP.NET yapılandırma dil, tek tek Hizmetleri için kullanılacak kültürü belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdc10-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="fdc10-335">WCF ASP.NET uyumluluk modunda, yapılandırma ayarı dışında desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fdc10-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="fdc10-336">ASP.NET uyumluluk modunun kullanılmaması bir WCF Hizmeti yerelleştirmek için hizmet türü kültüre özgü derlemeler içine derleyin ve her bir kültüre özgü derleme için ayrı kültüre özgü uç sahip.</span><span class="sxs-lookup"><span data-stu-id="fdc10-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc10-337">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc10-337">See also</span></span>
- [<span data-ttu-id="fdc10-338">ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fdc10-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
