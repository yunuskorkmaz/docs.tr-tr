---
title: ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c6e83bb234751dc477776f0fa540ffa8688dc667
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597598"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="442d0-102">ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="442d0-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="442d0-103">Windows Communication Foundation (WCF), WCF uygulamalarının ASP.NET Web Hizmetleri gibi programlanmış ve yapılandırılmış olmasını sağlamak ve davranışlarını taklit etmek için bir ASP.NET uyumluluk modu seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="442d0-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="442d0-104">Aşağıdaki bölümlerde, her iki teknolojiyi de kullanarak uygulama geliştirmek için gereklere bağlı olarak ASP.NET Web Hizmetleri ve WCF karşılaştırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="442d0-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="442d0-105">Veri gösterimi</span><span class="sxs-lookup"><span data-stu-id="442d0-105">Data Representation</span></span>

<span data-ttu-id="442d0-106">Bir Web hizmetinin ASP.NET ile geliştirilmesi genellikle hizmetin kullanacağı karmaşık veri türlerini tanımlamaya başlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="442d0-107">ASP.NET, <xref:System.Xml.Serialization.XmlSerializer> bir hizmete veya bir hizmete iletim için .NET Framework türleri tarafından temsil edilen VERILERI XML 'e çevirmek ve XML olarak alınan verileri .NET Framework nesnelerine dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="442d0-108">Bir ASP.NET hizmetinin kullanacağı karmaşık veri türlerini tanımlama, <xref:System.Xml.Serialization.XmlSerializer> XML 'den ve öğesinden seri hale getirebilen .NET Framework sınıflarının tanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="442d0-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="442d0-109">Bu tür sınıflar el ile yazılabilir veya komut satırı XML şemaları/veri türleri destek yardımcı programı olan xsd. exe kullanılarak XML şemasında türlerin tanımlarından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="442d0-110">Aşağıda, <xref:System.Xml.Serialization.XmlSerializer> XML 'den ve öğesinden seri hale getirebilen .NET Framework sınıfları tanımlarken bildiğiniz önemli sorunların bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="442d0-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="442d0-111">Yalnızca .NET Framework nesnelerinin ortak alanları ve özellikleri XML olarak çevrilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="442d0-112">Koleksiyon sınıflarının örnekleri yalnızca, sınıflar veya arabirimini uygularsa XML olarak seri hale getirilebilir <xref:System.Collections.IEnumerable> <xref:System.Collections.ICollection> .</span><span class="sxs-lookup"><span data-stu-id="442d0-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="442d0-113">Arabirimini uygulayan sınıflar, gibi <xref:System.Collections.IDictionary> <xref:System.Collections.Hashtable> , XML içine serileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="442d0-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="442d0-114">Ad alanındaki harika birçok öznitelik türü, <xref:System.Xml.Serialization> sınıf ÖRNEKLERININ XML 'de nasıl temsil edileceğini denetlemek için bir .NET Framework sınıfına ve üyelerine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="442d0-115">WCF uygulama geliştirme genellikle karmaşık türlerin tanımıyla de başlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="442d0-116">WCF, ASP.NET Web Hizmetleri ile aynı .NET Framework türlerini kullanacak şekilde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="442d0-117">WCF <xref:System.Runtime.Serialization.DataContractAttribute> ve, <xref:System.Runtime.Serialization.DataMemberAttribute> TÜRÜN örneklerinin XML 'e serileştirilmekte olduğunu ve aşağıdaki örnek kodda gösterildiği gibi türün hangi belirli alan veya özelliklerinin serileştirildiğine işaret etmek için .NET Framework türlerine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

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

<span data-ttu-id="442d0-118"><xref:System.Runtime.Serialization.DataContractAttribute>Bir türün alan veya özelliklerinin sıfır veya daha fazla seri hale getirildiğini, ancak <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alanın veya özelliğin serileştirilme olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="442d0-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="442d0-119"><xref:System.Runtime.Serialization.DataContractAttribute>Bir sınıfa veya yapıya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="442d0-120">, <xref:System.Runtime.Serialization.DataMemberAttribute> Bir alana veya özelliğe uygulanabilir ve özniteliğin uygulandığı alanlar ve Özellikler herkese açık veya özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="442d0-121">Bunlara uygulanmış olan türlerin örnekleri, <xref:System.Runtime.Serialization.DataContractAttribute> WCF 'de veri sözleşmeleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="442d0-122">Kullanılarak XML olarak serileştirilir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="442d0-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="442d0-123">Aşağıda, kullanarak <xref:System.Runtime.Serialization.DataContractSerializer> ve diğer <xref:System.Xml.Serialization.XmlSerializer> ad alanının çeşitli özniteliklerinin kullanılmasıyla arasındaki önemli farklılıkların bir listesi verilmiştir <xref:System.Xml.Serialization> .</span><span class="sxs-lookup"><span data-stu-id="442d0-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="442d0-124"><xref:System.Xml.Serialization.XmlSerializer>Ve <xref:System.Xml.Serialization> ad alanının öznitelikleri, .NET Framework türlerini XML şemasında tanımlanmış herhangi bir geçerli türle eşlemenizi sağlamak üzere tasarlanmıştır ve bu nedenle BIR türün XML 'de nasıl temsil edildiği konusunda çok kesin bir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="442d0-125"><xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> bir türün XML 'de nasıl temsil edildiği konusunda çok az denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="442d0-126">Yalnızca türü ve içindeki alanları ya da özellikleri temsil etmek için kullanılan ad alanlarını ve adları, XML 'de alan ve özelliklerin bulunduğu diziyi belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="442d0-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

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

  <span data-ttu-id="442d0-127">.NET türünü temsil etmek için kullanılan XML yapısına ilişkin diğer her şey, tarafından belirlenir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="442d0-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="442d0-128">Bir türün XML 'de nasıl temsil edildiği konusunda çok fazla denetime izin verilmez, serileştirme işlemi için yüksek düzeyde öngörülebilir hale gelir ve bu <xref:System.Runtime.Serialization.DataContractSerializer> nedenle iyileştirilmesi kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="442d0-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="442d0-129">Tasarımının pratik bir avantajı <xref:System.Runtime.Serialization.DataContractSerializer> daha iyi performans, yaklaşık yüzde on daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="442d0-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="442d0-130">İle birlikte kullanılacak öznitelikleri, <xref:System.Xml.Serialization.XmlSerializer> türünün hangi alanların veya ÖZELLIKLERIN XML olarak serileştirildiği göstermez, <xref:System.Runtime.Serialization.DataMemberAttribute> için için öğesinin, <xref:System.Runtime.Serialization.DataContractSerializer> açıkça hangi alanların veya özelliklerin serileştirildiği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="442d0-131">Bu nedenle, veri sözleşmeleri, bir uygulamanın gönderileceği ve alınacağı verilerin yapısı hakkında açık sözleşmelerdir.</span><span class="sxs-lookup"><span data-stu-id="442d0-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="442d0-132"><xref:System.Xml.Serialization.XmlSerializer>Yalnızca bir .NET nesnesinin ortak ÜYELERINI XML 'e çevirebilir, <xref:System.Runtime.Serialization.DataContractSerializer> Bu üyelerin erişim değiştiricilerinden bağımsız olarak nesne üyelerini XML 'e çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="442d0-133">Türlerin genel olmayan üyelerini XML olarak seri hale getirebilmek sonucunda, XML 'de seri hale geyebilen <xref:System.Runtime.Serialization.DataContractSerializer> çeşitli .net türlerinde daha az kısıtlama içerir.</span><span class="sxs-lookup"><span data-stu-id="442d0-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="442d0-134">Özellikle, arabirimini uygulayan gibi XML türlerine çeviri yapabilir <xref:System.Collections.Hashtable> <xref:System.Collections.IDictionary> .</span><span class="sxs-lookup"><span data-stu-id="442d0-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="442d0-135">, <xref:System.Runtime.Serialization.DataContractSerializer> Türün tanımını değiştirmek veya bir sarmalayıcı geliştirmek zorunda kalmadan, önceden var olan herhangi bir .NET türünün ÖRNEKLERINI XML olarak seri hale getirmek çok daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="442d0-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="442d0-136"><xref:System.Runtime.Serialization.DataContractSerializer>Bir türün genel olmayan üyelerine erişebilmekte olan başka bir sonuç ise tam güven gerektirmesidir, ancak bunu yapmaz <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="442d0-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="442d0-137">Tam güven kodu erişim izni, kodun yürütüldüğü kimlik bilgileri kullanılarak erişilebilen bir makinedeki tüm kaynaklara tam erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="442d0-138">Tam güvenilir kod, makinenizde bulunan tüm kaynaklara eriştiği için bu seçenek dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="442d0-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="442d0-139">, <xref:System.Runtime.Serialization.DataContractSerializer> Sürüm oluşturma için bazı destek içerir:</span><span class="sxs-lookup"><span data-stu-id="442d0-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="442d0-140">, <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Önceki sürümlerde mevcut olmayan bir veri sözleşmesinin yeni sürümlerine eklenen üyeler için yanlış değeri atanabilen bir özelliğe sahiptir ve böylece sözleşmenin daha yeni sürümüne sahip uygulamaların önceki sürümleri işleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="442d0-141">Bir veri sözleşmesinin <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimini uygulaması sayesinde, bir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesinin daha yeni sürümlerinde tanımlanan üyelerin, sözleşmenin önceki sürümleriyle uygulamalar aracılığıyla geçişine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="442d0-142">Tüm farklılıklara rağmen, <xref:System.Xml.Serialization.XmlSerializer> Varsayılan olarak bir türü seri hale getirilen XML, <xref:System.Runtime.Serialization.DataContractSerializer> bir türü seri hale getirilen XML ile aynıdır, ancak XML için ad alanı açıkça tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="442d0-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="442d0-143">Her iki serileştiriciyle birlikte kullanılmak üzere öznitelikleri olan aşağıdaki sınıf, ile ve arasında anlamsal özdeş XML 'e çevrilir <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="442d0-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

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

<span data-ttu-id="442d0-144">Windows yazılım geliştirme seti (SDK), [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)adlı bir komut satırı aracı içerir.</span><span class="sxs-lookup"><span data-stu-id="442d0-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="442d0-145">ASP.NET Web hizmetleriyle kullanılan xsd. exe aracı gibi, Svcutil. exe, XML şemasından .NET veri türlerinin tanımlarını oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="442d0-146">Türler, XML <xref:System.Runtime.Serialization.DataContractSerializer> şeması tarafından tanımlanan BIÇIMDE XML yayıyorsa, veri sözleşmelerdir; Aksi takdirde, kullanılarak serileştirme amaçlıdır <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="442d0-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="442d0-147">Svcutil. exe, kendi anahtarını kullanarak veri sözleşmelerinden bir XML şeması da oluşturabilir `dataContractOnly` .</span><span class="sxs-lookup"><span data-stu-id="442d0-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="442d0-148">ASP.NET Web Hizmetleri tarafından kullanılsa da WCF <xref:System.Xml.Serialization.XmlSerializer> ASP.NET uyumluluk modu, WCF hizmetleri ASP.NET Web hizmetlerinin davranışını taklit etse de ASP.NET uyumluluk seçeneği, bir ile kullanımını kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="442d0-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="442d0-149">Bunlardan biri, <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetlerini kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="442d0-150">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="442d0-150">Service Development</span></span>

<span data-ttu-id="442d0-151">ASP.NET kullanarak bir hizmet geliştirmek için, <xref:System.Web.Services.WebService> özniteliği bir sınıfa eklemek ve <xref:System.Web.Services.WebMethodAttribute> hizmetin işlemleri olması gereken sınıf ' metotlarından birine eklemektir:</span><span class="sxs-lookup"><span data-stu-id="442d0-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

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

<span data-ttu-id="442d0-152">ASP.NET 2,0, <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> bir sınıfı yerine özniteliği ve bir arabirime ekleme ve arabirimi uygulamak için bir sınıf yazma seçeneğini sunmuştur:</span><span class="sxs-lookup"><span data-stu-id="442d0-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

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

<span data-ttu-id="442d0-153">Bu seçeneğin kullanılması tercih edilmelidir çünkü özniteliğe sahip arabirim, <xref:System.Web.Services.WebService> hizmet tarafından gerçekleştirilen işlemler için, aynı sözleşmeyi farklı yollarla uygulayabilecek çeşitli sınıflarla yeniden kullanılabilen işlemler için bir sözleşme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="442d0-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="442d0-154">Bir veya daha fazla WCF uç noktası tanımlayarak bir WCF hizmeti sağlanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="442d0-155">Bir uç nokta, bir adres, bağlama ve hizmet sözleşmesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="442d0-156">Adres, hizmetin nerede olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-156">The address defines where the service is located.</span></span> <span data-ttu-id="442d0-157">Bağlama, hizmetle nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="442d0-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="442d0-158">Hizmet sözleşmesi, hizmetin gerçekleştirebileceği işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="442d0-159">Hizmet sözleşmesi genellikle, bir arabirim eklenerek ve ' den önce tanımlanmıştır <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="442d0-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="442d0-160"><xref:System.ServiceModel.ServiceContractAttribute>Arabirimin BIR WCF hizmeti sözleşmesi tanımladığını ve <xref:System.ServiceModel.OperationContractAttribute> arabirimin yöntemlerinin, varsa hizmet sözleşmesinin işlemlerini tanımladığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="442d0-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="442d0-161">Bir hizmet sözleşmesi tanımlandıktan sonra, sınıfı hizmet sözleşmesinin tanımlandığı arabirimi uygulayarak bir sınıfta uygulanır:</span><span class="sxs-lookup"><span data-stu-id="442d0-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="442d0-162">Bir hizmet sözleşmesini uygulayan bir sınıf, WCF 'de hizmet türü olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="442d0-163">Bir sonraki adım, bir adresi ve bağlamayı bir hizmet türüyle ilişkilendirmekte.</span><span class="sxs-lookup"><span data-stu-id="442d0-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="442d0-164">Bu, genellikle dosyayı doğrudan düzenleyerek veya WCF ile birlikte sunulan bir yapılandırma Düzenleyicisi kullanılarak bir yapılandırma dosyasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="442d0-165">Yapılandırma dosyasına bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="442d0-165">Here is an example of a configuration file.</span></span>

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

<span data-ttu-id="442d0-166">Bağlama, uygulamayla iletişim kurmak için protokoller kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="442d0-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="442d0-167">Aşağıdaki tabloda, genel seçenekleri temsil eden sistem tarafından sunulan bağlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="442d0-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="442d0-168">Name</span><span class="sxs-lookup"><span data-stu-id="442d0-168">Name</span></span>|<span data-ttu-id="442d0-169">Amaç</span><span class="sxs-lookup"><span data-stu-id="442d0-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="442d0-170">Kullanmayı</span><span class="sxs-lookup"><span data-stu-id="442d0-170">BasicHttpBinding</span></span>|<span data-ttu-id="442d0-171">WS-BasicProfile 1,1 ve temel güvenlik profili 1,0 ' i destekleyen Web Hizmetleri ve istemcilerle birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="442d0-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="442d0-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-172">WSHttpBinding</span></span>|<span data-ttu-id="442d0-173">HTTP üzerinden WS-\* protokollerini destekleyen Web Hizmetleri ve istemcilerle birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="442d0-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="442d0-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-174">WSDualHttpBinding</span></span>|<span data-ttu-id="442d0-175">Bir ilk ileti alıcısının doğrudan ilk gönderene yanıt içermediği, ancak bir süre içinde, WS-\* protokolleriyle birlikte HTTP kullanarak istediğiniz sayıda yanıtı aktarabileceği çift yönlü HTTP iletişimi.</span><span class="sxs-lookup"><span data-stu-id="442d0-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="442d0-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-176">WSFederationBinding</span></span>|<span data-ttu-id="442d0-177">Bir hizmetin kaynaklarına erişimin, açıkça tanımlanmış bir kimlik bilgisi sağlayıcısı tarafından verilen kimlik bilgilerine göre denetlenebileceği HTTP iletişimi.</span><span class="sxs-lookup"><span data-stu-id="442d0-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="442d0-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-178">NetTcpBinding</span></span>|<span data-ttu-id="442d0-179">Ağ genelindeki WCF yazılım varlıkları arasında güvenli, güvenilir, yüksek performanslı iletişim.</span><span class="sxs-lookup"><span data-stu-id="442d0-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="442d0-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="442d0-181">Aynı makinede WCF yazılım varlıkları arasında güvenli, güvenilir, yüksek performanslı iletişim.</span><span class="sxs-lookup"><span data-stu-id="442d0-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="442d0-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-182">NetMsmqBinding</span></span>|<span data-ttu-id="442d0-183">MSMQ kullanarak WCF yazılım varlıkları arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="442d0-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="442d0-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="442d0-185">Bir WCF yazılım varlığı ile başka bir yazılım varlığı arasında MSMQ kullanarak iletişim.</span><span class="sxs-lookup"><span data-stu-id="442d0-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="442d0-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="442d0-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="442d0-187">Windows Eşler arası ağ kullanarak WCF yazılım varlıkları arasında iletişim.</span><span class="sxs-lookup"><span data-stu-id="442d0-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="442d0-188">Sistem tarafından sunulan bağlama, <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web Hizmetleri tarafından desteklenen protokol kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="442d0-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="442d0-189">WCF uygulamaları için özel bağlamalar, WCF 'nin tek tek protokolleri uygulamak için kullandığı bağlama öğesi sınıflarının koleksiyonları olarak kolayca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="442d0-190">Yeni bağlama öğeleri, ek protokolleri temsil etmek için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="442d0-191">Hizmet türlerinin iç davranışı, davranışlar adlı bir sınıf ailesinin özellikleri kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="442d0-192">Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıf, hizmet türünün çok iş parçacıklı olduğunu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="442d0-193">Gibi bazı davranışlar <xref:System.ServiceModel.ServiceBehaviorAttribute> öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="442d0-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="442d0-194">Kullanıcılar, yöneticilerin ayarlamak istedikleri özelliklere sahip olanlar, bir uygulamanın yapılandırmasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="442d0-195">Programlama hizmeti türlerinde, sınıfının sık kullanılan kullanımı yapılır <xref:System.ServiceModel.OperationContext> .</span><span class="sxs-lookup"><span data-stu-id="442d0-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="442d0-196">Statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği, bir işlemin çalıştığı bağlam hakkındaki bilgilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="442d0-197"><xref:System.ServiceModel.OperationContext>, <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıflarına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="442d0-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="442d0-198">Hosting</span><span class="sxs-lookup"><span data-stu-id="442d0-198">Hosting</span></span>

<span data-ttu-id="442d0-199">ASP.NET Web Hizmetleri bir sınıf kitaplığı derlemesine derlenir.</span><span class="sxs-lookup"><span data-stu-id="442d0-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="442d0-200">Service File adlı bir dosya,. asmx uzantısına sahiptir ve `@ WebService` hizmet için kodu ve bulunduğu derlemeyi içeren sınıfı tanımlayan bir yönerge içerir.</span><span class="sxs-lookup"><span data-stu-id="442d0-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="442d0-201">Hizmet dosyası Internet Information Services (IIS) içinde bir ASP.NET uygulama köküne kopyalanır ve derleme bu uygulama kökünün \bin alt dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="442d0-202">Daha sonra uygulama, uygulama kökündeki hizmet dosyasının Tekdüzen Kaynak Konum Belirleyicisi (URL) kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="442d0-203">WCF Hizmetleri IIS 5,1 veya 6,0 ' de, IIS 7,0 'nin bir parçası olarak sunulan Windows Işlem etkinleştirme hizmeti (WAS) ve herhangi bir .NET uygulaması içinde kolayca barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="442d0-204">IIS 5,1 veya 6,0 ' de bir hizmeti barındırmak için hizmetin iletişim aktarım protokolü olarak HTTP kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="442d0-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="442d0-205">IIS 5,1, 6,0 veya içinde bir hizmet barındırmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="442d0-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="442d0-206">Hizmet türünü bir sınıf kitaplığı derlemesinde derleyin.</span><span class="sxs-lookup"><span data-stu-id="442d0-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="442d0-207">Hizmet türünü tanımlamak için bir yönergesi ile. svc uzantılı bir hizmet dosyası oluşturun `@ ServiceHost` :</span><span class="sxs-lookup"><span data-stu-id="442d0-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="442d0-208">Hizmet dosyasını bir sanal dizine ve derlemeye bu sanal dizinin \bin alt dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="442d0-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="442d0-209">Yapılandırma dosyasını sanal dizine kopyalayın ve Web. config olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="442d0-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="442d0-210">Uygulamaya daha sonra uygulama kökündeki hizmet dosyasının URL 'SI kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="442d0-211">Bir .NET uygulamasında bir WCF hizmetini barındırmak için, hizmet türünü uygulama tarafından başvurulan bir sınıf kitaplığı derlemesinde derleyin ve uygulamayı, sınıfı kullanarak hizmeti barındıracak şekilde programlayabilirsiniz <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="442d0-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="442d0-212">Aşağıdakiler, gerekli temel programlama örneğidir:</span><span class="sxs-lookup"><span data-stu-id="442d0-212">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="442d0-213">Bu örnek, bir veya daha fazla Aktarım Protokolü adresinin bir oluşturma sırasında nasıl belirtildiği gösterilmektedir <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="442d0-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="442d0-214">Bu adreslere taban adresler denir.</span><span class="sxs-lookup"><span data-stu-id="442d0-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="442d0-215">WCF hizmetinin herhangi bir uç noktası için belirtilen adres, uç noktanın ana adresinin temel adresiyle ilişkili bir adrestir.</span><span class="sxs-lookup"><span data-stu-id="442d0-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="442d0-216">Ana bilgisayar her iletişim Aktarım Protokolü için bir temel adrese sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="442d0-217">Önceki yapılandırma dosyasındaki örnek yapılandırmada, <xref:System.ServiceModel.BasicHttpBinding> uç nokta için seçilen, aktarım protokolü olarak http 'yi kullanır, bu nedenle uç noktanın adresi `EchoService` ana bilgisayarın http taban adresine görelidir.</span><span class="sxs-lookup"><span data-stu-id="442d0-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="442d0-218">Yukarıdaki örnekteki ana bilgisayar söz konusu olduğunda, HTTP temel adresi olur `http://www.contoso.com:8000/` .</span><span class="sxs-lookup"><span data-stu-id="442d0-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="442d0-219">IIS veya WAS içinde barındırılan bir hizmet için temel adres, hizmetin hizmet dosyasının URL 'sidir.</span><span class="sxs-lookup"><span data-stu-id="442d0-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="442d0-220">Yalnızca IIS veya WAS 'da barındırılan ve yalnızca Aktarım Protokolü olarak HTTP ile yapılandırılmış olan hizmetler, WCF ASP.NET uyumluluk modu seçeneğini kullanacak şekilde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="442d0-221">Bu seçeneği açık olarak açmak aşağıdaki adımları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="442d0-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="442d0-222">Programcının <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> özniteliği hizmet türüne eklemesi ve ASP.NET uyumluluk modunun izin verileceğini veya gerekli olduğunu belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="442d0-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="442d0-223">Yöneticinin uygulamayı ASP.NET uyumluluk modunu kullanacak şekilde yapılandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="442d0-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

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

    <span data-ttu-id="442d0-224">WCF uygulamaları,. svc yerine hizmet dosyaları için uzantısı olarak. asmx kullanacak şekilde de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="442d0-225">Bu seçenek, WCF 'yi kullanmak üzere bir hizmeti değiştirirken. asmx hizmet dosyalarının URL 'Lerini kullanmak üzere yapılandırılmış istemcileri değiştirmenize gerek kalmadan sizi kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="442d0-226">İstemci Geliştirme</span><span class="sxs-lookup"><span data-stu-id="442d0-226">Client Development</span></span>

<span data-ttu-id="442d0-227">ASP.NET Web Hizmetleri için istemciler,. asmx dosyasının URL 'sini girdi olarak sağlayan WSDL. exe komut satırı aracı kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="442d0-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="442d0-228">WCF tarafından sunulan ilgili araç [ServiceModel meta veri yardımcı programı aracıdır (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="442d0-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="442d0-229">Hizmet sözleşmesinin tanımına ve bir WCF istemci sınıfının tanımına sahip bir kod modülü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="442d0-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="442d0-230">Ayrıca, hizmetin adresi ve bağlamasını içeren bir yapılandırma dosyası da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="442d0-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="442d0-231">Uzak bir hizmetin istemcisinin programlama aşamasında, genellikle zaman uyumsuz bir modele göre programlanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="442d0-232">WSDL. exe aracı tarafından oluşturulan kod her zaman hem zaman uyumlu hem de zaman uyumsuz bir model için varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="442d0-233">[ServiceModel meta veri yardımcı programı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan kod, her iki model için de sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="442d0-234">Varsayılan olarak zaman uyumlu model sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="442d0-235">Araç, anahtarla yürütülürse `/async` , oluşturulan kod zaman uyumsuz model için sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="442d0-236">ASP tarafından oluşturulan WCF istemci sınıflarında adların garantisi yoktur. NET ' in WSDL. exe aracı, varsayılan olarak, Svcutil. exe aracı tarafından oluşturulan WCF istemci sınıflarında adları eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="442d0-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="442d0-237">Özellikle, kullanılarak serileştirilmesi gereken sınıfların özelliklerinin adları, <xref:System.Xml.Serialization.XmlSerializer> Varsayılan olarak, WSDL. exe aracında bir durum olmayan Svcutil. exe aracı tarafından oluşturulan koddaki sonek özelliği verilirler.</span><span class="sxs-lookup"><span data-stu-id="442d0-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="442d0-238">İleti temsili</span><span class="sxs-lookup"><span data-stu-id="442d0-238">Message Representation</span></span>

<span data-ttu-id="442d0-239">ASP.NET Web Hizmetleri tarafından gönderilen ve alınan SOAP iletilerinin üstbilgileri özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="442d0-240">Bir sınıf, <xref:System.Web.Services.Protocols.SoapHeader> üstbilginin yapısını tanımlamak için öğesinden türetilir ve sonra <xref:System.Web.Services.Protocols.SoapHeaderAttribute> üstbilginin varlığını göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

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

<span data-ttu-id="442d0-241">WCF, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> bir hizmet tarafından GÖNDERILEN ve alınan SOAP iletilerinin yapısını betimleyen,, ve özniteliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

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
public class ItemMessage
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

<span data-ttu-id="442d0-242">Bu sözdizimi, iletilerin yapısının açık bir gösterimini verir, ancak iletilerin yapısı bir ASP.NET Web hizmeti kodu tarafından kapsanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="442d0-243">Ayrıca, ASP.NET sözdiziminde, ileti üstbilgileri hizmetin özellikleri olarak temsil edilir (örneğin, `ProtocolHeader` önceki örnekteki özelliği), WCF sözdiziminde, iletilerin özellikleri olarak daha doğru şekilde temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="442d0-244">Ayrıca, WCF, ileti üstbilgilerinin uç noktaların yapılandırmasına eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="442d0-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

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

<span data-ttu-id="442d0-245">Bu seçenek, bir istemci veya hizmet için koddaki altyapısal protokol üst bilgilerine yönelik herhangi bir başvuruyu önlemenize olanak sağlar: uç noktanın nasıl yapılandırıldığına ilişkin olarak üstbilgiler iletilere eklenir.</span><span class="sxs-lookup"><span data-stu-id="442d0-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="442d0-246">Hizmet Açıklaması</span><span class="sxs-lookup"><span data-stu-id="442d0-246">Service Description</span></span>

<span data-ttu-id="442d0-247">ASP.NET bir Web hizmetinin. asmx dosyası için bir HTTP GET isteği verme, WSDL sorgusu, ASP.NET 'nin hizmeti betimleyen WSDL oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="442d0-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="442d0-248">İsteğin yanıtı olarak WSDL döndürür.</span><span class="sxs-lookup"><span data-stu-id="442d0-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="442d0-249">ASP.NET 2,0, bir hizmetin Web Hizmetleri ile birlikte çalışabilirlik kuruluşunun (WS-ı) 1,1 temel profiliyle uyumlu olduğunu doğrulamak ve hizmetin WSDL 'ye uyumlu olduğunu bir talep eklemek mümkün hale gelir.</span><span class="sxs-lookup"><span data-stu-id="442d0-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="442d0-250">Bu, `ConformsTo` özniteliğinin ve parametreleri kullanılarak yapılır `EmitConformanceClaims` <xref:System.Web.Services.WebServiceBindingAttribute> .</span><span class="sxs-lookup"><span data-stu-id="442d0-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="442d0-251">Bir hizmet için ASP.NET üreten WSDL özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="442d0-252">Özelleştirmeler <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> , WSDL 'ye öğe eklemek için türetilmiş bir sınıfı oluşturularak yapılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="442d0-253">IIS 51, 6,0 veya üzerinde barındırılan bir HTTP uç noktası ile bir WCF hizmetinin. svc dosyası için WSDL sorgu WSDL ile HTTP GET isteği verme, WCF 'nin hizmeti tanımlamasını sağlamak üzere WSDL ile yanıt vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="442d0-254">HttpGetEnabled, true olarak ayarlandıysa, bir .NET uygulaması içinde barındırılan bir hizmetin HTTP taban adresine WSDL ile bir HTTP GET isteği verilmesi aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="442d0-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="442d0-255">Bununla birlikte, WCF Ayrıca bir hizmeti tanımlamaya yönelik oluşturduğu WSDL ile WS-MetadataExchange isteklerini de yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="442d0-256">ASP.NET Web Hizmetleri, WS-MetadataExchange istekleri için yerleşik desteğe sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="442d0-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="442d0-257">WCF tarafından oluşturulacak WSDL, kapsamlı bir şekilde özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="442d0-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior>Sınıfı, WSDL 'yi özelleştirmek için bazı tesisler sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="442d0-259">WCF Ayrıca, WSDL oluşturmak için yapılandırılabilir, ancak belirli bir URL 'de statik bir WSDL dosyası kullanmak yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

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

## <a name="exception-handling"></a><span data-ttu-id="442d0-260">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="442d0-260">Exception Handling</span></span>

<span data-ttu-id="442d0-261">ASP.NET Web hizmetlerinde, işlenmemiş özel durumlar istemcilere SOAP hatası olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="442d0-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="442d0-262">Ayrıca, sınıfının örneklerini açıkça oluşturabilir <xref:System.Web.Services.Protocols.SoapException> ve istemciye ILETILEN SOAP hatasının içeriği üzerinde daha fazla denetime sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="442d0-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="442d0-263">WCF hizmetlerinde, önemli bilgilerin yanlışlıkla özel durumlar üzerinden gösterilmesini engellemek için işlenmemiş özel durumlar istemcilere SOAP hatası olarak döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="442d0-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="442d0-264">Bir yapılandırma ayarı, istemcilere hata ayıklama amacıyla geri döndürülen işlenmemiş özel durumları sağlamak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="442d0-265">İstemcilere SOAP hataları döndürmek için, genel tür <xref:System.ServiceModel.FaultException%601> olarak veri sözleşmesi türünü kullanarak genel türün örneklerini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="442d0-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="442d0-266">Ayrıca, <xref:System.ServiceModel.FaultContractAttribute> bir işlemin sağlayabileceği hataları belirtmek için işlemlere öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="442d0-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

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

<span data-ttu-id="442d0-267">Bunun yapılması, hizmet için WSDL 'de tanıtılmakta olan hataların, istemci programcılarının hangi hataların bir işlemden neden olduğunu tahmin etmesinin yanı sıra uygun catch deyimlerini yazabileceğini tahmin etmenize neden olur.</span><span class="sxs-lookup"><span data-stu-id="442d0-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

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

## <a name="state-management"></a><span data-ttu-id="442d0-268">Durum yönetimi</span><span class="sxs-lookup"><span data-stu-id="442d0-268">State Management</span></span>

<span data-ttu-id="442d0-269">Bir ASP.NET Web hizmetini uygulamak için kullanılan sınıf öğesinden türetilebilir <xref:System.Web.Services.WebService> .</span><span class="sxs-lookup"><span data-stu-id="442d0-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="442d0-270">Bu durumda, sınıfı <xref:System.Web.Services.WebService> bir nesneye erişmek için temel sınıfın ' Context özelliğini kullanmak üzere programlanabilir <xref:System.Web.HttpContext> .</span><span class="sxs-lookup"><span data-stu-id="442d0-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="442d0-271">Nesnesi, uygulama <xref:System.Web.HttpContext> özelliği kullanılarak uygulama durumu bilgilerini güncelleştirmek ve almak için kullanılabilir ve oturum özelliğini kullanarak oturum durumu bilgilerini güncelleştirmek ve almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="442d0-272">ASP.NET, uygulamasının oturum durumu bilgilerinin, aslında ' ın Session özelliği kullanılarak eriştiği konuma göre önemli bir denetim sağlar <xref:System.Web.HttpContext> .</span><span class="sxs-lookup"><span data-stu-id="442d0-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="442d0-273">Tanımlama bilgilerinde, bir veritabanında, geçerli sunucu belleğinde veya belirlenen bir sunucunun belleğinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="442d0-274">Bu seçenek, hizmetin yapılandırma dosyasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="442d0-275">WCF, durum yönetimi için Genişletilebilir nesneler sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="442d0-276">Genişletilebilir nesneler, uygulayan nesnelerdir <xref:System.ServiceModel.IExtensibleObject%601> .</span><span class="sxs-lookup"><span data-stu-id="442d0-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="442d0-277">En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve ' dir <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="442d0-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="442d0-278">`ServiceHostBase`aynı ana bilgisayardaki tüm hizmet türlerinin tümünün erişebileceği durumu korumanıza olanak sağlar, ancak `InstanceContext` aynı hizmet türü örneğinde çalışan herhangi bir kod tarafından erişilebilen durumu korumanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="442d0-279">Burada, hizmet türü, `TradingSystem` <xref:System.ServiceModel.ServiceBehaviorAttribute> aynı WCF istemci örneğindeki tüm çağrıların hizmet türünün aynı örneğine yönlendirildiğini belirten bir içerir.</span><span class="sxs-lookup"><span data-stu-id="442d0-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="442d0-280">Sınıfı, `DealData` bir hizmet türünün aynı örneğinde çalışan herhangi bir kod tarafından erişilebilen durumu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="442d0-281">Hizmet sözleşmesinin işlemlerinden birini uygulayan hizmet türünün kodunda, `DealData` hizmet türünün geçerli örneğinin durumuna bir durum nesnesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="442d0-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="442d0-282">Bu durum nesnesi daha sonra hizmet sözleşmesinin işlemlerini uygulayan kod tarafından alınabilir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="442d0-283">ASP.NET, sınıftaki durum bilgilerinin <xref:System.Web.HttpContext> gerçekten depolandığı, WCF 'nin en azından ilk sürümünde, Genişletilebilir nesnelerin depolandığı yerde denetim sunmayacak şekilde denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="442d0-284">Bu, bir WCF hizmeti için ASP.NET uyumluluk modunu seçmenin en iyi nedenini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="442d0-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="442d0-285">Yapılandırılabilir durum yönetimi gerekliyse, ASP.NET uyumluluk modu için kullanılması, sınıfın tesislerini <xref:System.Web.HttpContext> ASP.net ' de kullanıldıkları şekilde kullanmanıza ve ayrıca sınıfı kullanılarak yönetilen durum bilgilerinin nerede depolandığını yapılandırmanıza olanak tanır <xref:System.Web.HttpContext> .</span><span class="sxs-lookup"><span data-stu-id="442d0-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="442d0-286">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="442d0-286">Security</span></span>

<span data-ttu-id="442d0-287">ASP.NET Web hizmetlerini güvenli hale getirmek için seçenekler, herhangi bir IIS uygulamasının güvenliğini sağlamaya yönelik olanlardır.</span><span class="sxs-lookup"><span data-stu-id="442d0-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="442d0-288">WCF uygulamaları yalnızca IIS içinde değil, ancak herhangi bir .NET yürütülebilir dosyası içinde barındırılabilecek olduğundan, WCF uygulamalarının güvenliğini sağlamaya yönelik seçenekler IIS 'nin tesislerden bağımsız yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="442d0-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="442d0-289">Ancak, ASP.NET Web Hizmetleri için sağlanan tesisler ASP.NET uyumluluk modunda çalışan WCF Hizmetleri için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="442d0-290">Güvenlik: kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="442d0-290">Security: Authentication</span></span>

<span data-ttu-id="442d0-291">IIS, anonim erişimi veya çeşitli kimlik doğrulama modlarını seçebileceğiniz uygulamalara erişimi denetlemek için tesis sağlar: Windows kimlik doğrulaması, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="442d0-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="442d0-292">Windows kimlik doğrulama seçeneği, ASP.NET Web hizmetlerine erişimi denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="442d0-293">Ancak, WCF uygulamaları IIS içinde barındırılıyorsa, IIS 'nin uygulamaya anonim erişime izin verecek şekilde yapılandırılması gerekir, böylece kimlik doğrulaması, diğer çeşitli seçenekler arasında Windows kimlik doğrulamasını destekler.</span><span class="sxs-lookup"><span data-stu-id="442d0-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="442d0-294">Yerleşik diğer seçenekler Kullanıcı adı belirteçleri, X. 509.440 sertifikaları, SAML belirteçleri ve CardSpace kartını içerir, ancak özel kimlik doğrulama mekanizmaları de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="442d0-295">Güvenlik: kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="442d0-295">Security: Impersonation</span></span>

<span data-ttu-id="442d0-296">ASP.NET, belirli bir kullanıcının kimliğine bürünmek için bir ASP.NET Web hizmeti 'nin veya geçerli istekle ilgili kimlik bilgilerinin sağlandığı bir kimlik öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="442d0-297">Bu öğe, ASP.NET uyumluluk modunda çalışan WCF uygulamalarında kimliğe bürünme yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="442d0-298">WCF yapılandırma sistemi, belirli bir kullanıcıyı kimliğe bürünmek üzere atamak için kendi kimlik öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="442d0-299">Ayrıca, WCF istemcileri ve Hizmetleri, kimliğe bürünme için bağımsız olarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="442d0-300">İstemciler istekleri aktarırken geçerli kullanıcının kimliğine bürünmek üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="442d0-301">Hizmet işlemleri, geçerli istek ile hangi kullanıcının kimlik bilgilerinin sağlandığını taklit etmek üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="442d0-302">Güvenlik: Access Control listelerini kullanarak yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="442d0-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="442d0-303">Access Control listeleri (ACL 'Ler),. asmx dosyalarına erişimi kısıtlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="442d0-304">Bununla birlikte, WCF. svc dosyalarındaki ACL 'Ler ASP.NET uyumluluk modu dışında yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="442d0-305">Güvenlik: rol tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="442d0-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="442d0-306">IIS Windows kimlik doğrulaması seçeneği, kullanıcıların atandığı Windows gruplarını temel alan ASP.NET Web Hizmetleri için rol tabanlı yetkilendirmeyi kolaylaştırmak üzere ASP.NET yapılandırma dili tarafından sunulan yetkilendirme öğesiyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="442d0-307">ASP.NET 2,0, daha genel rol tabanlı bir yetkilendirme mekanizması sunmuştur: rol sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="442d0-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="442d0-308">Rol sağlayıcıları, bir kullanıcının atandığı roller hakkında temel bir arabirim uygulayan sınıflardır, ancak her bir rol sağlayıcısı bu bilgilerin farklı bir kaynaktan nasıl alınacağını bilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="442d0-309">ASP.NET 2,0, Microsoft SQL Server veritabanından rol atamalarını alan ve Windows Server 2003 Yetkilendirme Yöneticisi 'nden rol atamalarını alan bir rol sağlayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="442d0-310">Rol sağlayıcı mekanizması, WCF uygulaması da dahil olmak üzere herhangi bir .NET uygulamasında ASP.NET bağımsız olarak bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="442d0-311">Bir WCF uygulaması için aşağıdaki örnek yapılandırma, bir ASP.NET rol sağlayıcısının kullanımını, ' nin tarafından seçilen bir seçenek olduğunu gösterir <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="442d0-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

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

### <a name="security-claims-based-authorization"></a><span data-ttu-id="442d0-312">Güvenlik: talep tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="442d0-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="442d0-313">WCF 'nin en önemli yeniliklerinden biri, talebe göre korumalı kaynaklara erişimi yetkilendirmek için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="442d0-314">Talepler, örneğin, bir türü, bir sağ ve bir değer, bir sürücü lisansı olan bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="442d0-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="442d0-315">Taşıyıcı hakkında bir talepler kümesi oluşturur ve bunlardan biri, taşıyıcının Doğum tarihidir.</span><span class="sxs-lookup"><span data-stu-id="442d0-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="442d0-316">Bu talebin türü Doğum tarihidir, talebin değeri ise sürücünün Doğum tarihidir.</span><span class="sxs-lookup"><span data-stu-id="442d0-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="442d0-317">Bir talebin, taşıyıcının bu sırada ne yapabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="442d0-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="442d0-318">Sürücünün Doğum tarihi talebi söz konusu olduğunda, doğru sahip olur: sürücü söz konusu Doğum tarihine sahiptir ancak örneğin, bunu değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="442d0-319">Roller bir talep türü olduğundan, talep tabanlı yetkilendirme rol tabanlı yetkilendirmeyi barındırır.</span><span class="sxs-lookup"><span data-stu-id="442d0-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="442d0-320">Talepler temelinde yetkilendirme, bir talep kümesi, işlemin erişim gereksinimleriyle karşılaştırılarak ve bu karşılaştırmanın sonucuna bağlı olarak, işleme erişim izni verirken veya reddettikten sonra yapılır.</span><span class="sxs-lookup"><span data-stu-id="442d0-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="442d0-321">WCF 'de, özelliğine bir değer atayarak, talep tabanlı yetkilendirmeyi çalıştırmak için kullanılacak bir sınıf belirtebilirsiniz `ServiceAuthorizationManager` <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="442d0-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="442d0-322">Talep tabanlı yetkilendirmeyi çalıştırmak için kullanılan sınıflar <xref:System.ServiceModel.ServiceAuthorizationManager> , geçersiz kılmak için yalnızca bir yöntemi olan öğesinden türetilmelidir `AccessCheck()` .</span><span class="sxs-lookup"><span data-stu-id="442d0-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="442d0-323">WCF, her bir hizmet işlemi çağrıldığında bu yöntemi çağırır ve <xref:System.ServiceModel.OperationContext> , özelliği içinde Kullanıcı için talepler içeren bir nesne sağlar `ServiceSecurityContext.AuthorizationContext` .</span><span class="sxs-lookup"><span data-stu-id="442d0-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="442d0-324">WCF, kullanıcı hakkındaki talepleri, kullanıcının kimlik doğrulaması için verdiği herhangi bir güvenlik belirteciyle, bu taleplerin söz konusu işlem için yeterli olup olmadığını değerlendirme görevini atan bir kullanıcı hakkında bilgi veren çalışmalardır.</span><span class="sxs-lookup"><span data-stu-id="442d0-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="442d0-325">Bu WCF, her türlü güvenlik belirtecinin taleplerini otomatik olarak ayrıştırır. Bu, talebe dayalı olarak kimlik doğrulama mekanizmasından bağımsız olarak yetkilendirme kodu oluşturduğundan yüksek ölçüde önemli bir yeniliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="442d0-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="442d0-326">Bunun aksine, ASP.NET içindeki ACL 'Leri veya rolleri kullanarak yetkilendirme, Windows kimlik doğrulamasına yakından bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="442d0-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="442d0-327">Güvenlik: Gizlilik</span><span class="sxs-lookup"><span data-stu-id="442d0-327">Security: Confidentiality</span></span>

<span data-ttu-id="442d0-328">ASP.NET Web hizmetleriyle değiştirilen iletilerin gizliliği, IIS içindeki uygulamayı Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak Aktarım düzeyinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="442d0-329">IIS içinde barındırılan WCF uygulamaları için de aynı işlem yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="442d0-330">Ancak, IIS dışında barındırılan WCF uygulamaları da güvenli bir aktarım protokolü kullanacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="442d0-331">Daha önemli olan WCF uygulamaları, WS-Security protokolü kullanılarak, gönderilmeden önce iletilerin güvenliğini sağlamak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="442d0-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="442d0-332">WS-Security kullanarak yalnızca bir iletinin gövdesini güvenli hale getirmek, BT 'nin son hedefine ulaşmadan önce aracıların genelinde confidentially aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="442d0-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="442d0-333">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="442d0-333">Globalization</span></span>

<span data-ttu-id="442d0-334">ASP.NET yapılandırma dili, tek tek hizmetler için kültürü belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="442d0-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="442d0-335">WCF, ASP.NET uyumluluk modu dışında bu yapılandırma ayarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="442d0-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="442d0-336">ASP.NET uyumluluk modunu kullanmayan bir WCF hizmetini yerelleştirmek için, hizmet türünü kültüre özgü Derlemelerle derleyin ve kültüre özgü her derleme için kültüre özgü ayrı uç noktalara sahip yapın.</span><span class="sxs-lookup"><span data-stu-id="442d0-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="442d0-337">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="442d0-337">See also</span></span>

- [<span data-ttu-id="442d0-338">ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="442d0-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
