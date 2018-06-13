---
title: ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: fcf2d204d9d59a29024ff09d92be2a7b9339fce9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496656"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="b4c88-102">ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="b4c88-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
<span data-ttu-id="b4c88-103">Windows Communication Foundation (WCF) programlanmış ve ASP.NET Web Hizmetleri gibi yapılandırılması WCF uygulamaları etkinleştirmek ve davranışlarını taklit etmek için bir ASP.NET uyumluluk modu seçeneğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="b4c88-104">Aşağıdaki bölümlerde ASP.NET Web Hizmetleri karşılaştırın ve WCF ne iki teknolojiyi kullanarak uygulamaları geliştirmek için gerekli olduğuna bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="b4c88-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="b4c88-105">Veri temsili</span><span class="sxs-lookup"><span data-stu-id="b4c88-105">Data Representation</span></span>  
 <span data-ttu-id="b4c88-106">ASP.NET Web hizmetiyle geliştirme genellikle hizmet kullanmaktır herhangi karmaşık veri türlerini tanımlama ile başlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="b4c88-107">ASP.NET kullanır <xref:System.Xml.Serialization.XmlSerializer> iletim ya da hizmet için XML ve .NET Framework türleri tarafından gösterilen veriler Çevir ve .NET Framework nesnelerini XML olarak alınan veriler çevir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="b4c88-108">ASP.NET hizmeti kullanmaktır karmaşık veri türlerini tanımlama gerektiren .NET Framework'ün tanımı sınıfları <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden seri hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="b4c88-109">Bu tür sınıflar el ile yazılmış veya komut satırı XML şemaları/veri türleri destek yardımcı programı kullanarak XML şemasındaki türlerinin tanımlarını üretilen XSD.exe'nin.</span><span class="sxs-lookup"><span data-stu-id="b4c88-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="b4c88-110">Ne zaman .NET Framework tanımlayan sınıflar bilmeniz anahtar sorunların bir listesi aşağıda verilmiştir <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden seri hale getirebilir:</span><span class="sxs-lookup"><span data-stu-id="b4c88-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="b4c88-111">Yalnızca genel alanlar ve .NET Framework nesnelerin özelliklerini XML çevrilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="b4c88-112">Koleksiyon sınıfları örneklerini hale getirilebilir XML sınıflar ya da uygularsanız <xref:System.Collections.IEnumerable> veya <xref:System.Collections.ICollection> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b4c88-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="b4c88-113">Sınıfları uygulayan <xref:System.Collections.IDictionary> gibi arabirim <xref:System.Collections.Hashtable>, XML'de serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="b4c88-114">Çoğu öznitelik türlerinde mükemmel <xref:System.Xml.Serialization> ad alanı .NET Framework sınıf ve üyeleri sınıfın örnekleri, XML'de nasıl temsil edildiğini denetlemek için eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 <span data-ttu-id="b4c88-115">WCF uygulaması geliştirme de genellikle karmaşık türler tanımıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="b4c88-116">ASP.NET Web Hizmetleri olarak aynı .NET Framework türlerini kullanmak için WCF yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="b4c88-117">WCF<xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> türdeki örneklerin XML ve hangi belirli alanlar veya türünün özelliklerini serileştirilmesi için aşağıdaki örnek kodda gösterildiği gibi olduğundan seri hale olduğunu belirtmek için .NET Framework türleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-118"><xref:System.Runtime.Serialization.DataContractAttribute> Sıfır veya daha fazla bir tür alanları veya özellikler olmak anlamına gelir serileştirildiği while <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alan veya özelliği seri hale olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="b4c88-119"><xref:System.Runtime.Serialization.DataContractAttribute> Bir sınıf veya yapı uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="b4c88-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Bir alan veya bir özellik için uygulanabilir ve ortak veya özel alanlar ve öznitelik uygulanan özellikler olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="b4c88-121">Türleri örneklerini <xref:System.Runtime.Serialization.DataContractAttribute> uygulanan içinde WCF veri sözleşmeleri gibi bunları olarak denir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="b4c88-122">XML'de serileştirilir kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b4c88-123">Aşağıdaki kullanımı arasındaki önemli farklılıkları listesidir <xref:System.Runtime.Serialization.DataContractSerializer> ve kullanarak <xref:System.Xml.Serialization.XmlSerializer> ve çeşitli özniteliklerini <xref:System.Xml.Serialization> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b4c88-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="b4c88-124"><xref:System.Xml.Serialization.XmlSerializer> Ve özniteliklerini <xref:System.Xml.Serialization> ad alanı .NET Framework türleri XML Şeması'nda tanımlanan herhangi bir geçerli türüne eşlenir olanak tanımak için tasarlanmıştır ve bu nedenle sağlarlar türü XML'de nasıl temsil üzerinden çok kesin bir denetim için.</span><span class="sxs-lookup"><span data-stu-id="b4c88-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="b4c88-125"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> bir türü XML'de nasıl temsil üzerinde çok az denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="b4c88-126">Ad alanları ve türü ve alanlar veya XML ve alanlar ve Özellikler XML'de görünme sırasını özelliklerinde temsil etmek için kullanılan adları yalnızca belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b4c88-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="b4c88-127">Tarafından belirlenen şey .NET türü temsil etmek için kullanılan XML yapısı hakkında <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="b4c88-128">Nasıl bir XML dosyasında gösterilemeyecek kadar türüdür kadar denetim vermeyerek seri hale getirme işlemi için yüksek oranda tahmin edilebilir hale <xref:System.Runtime.Serialization.DataContractSerializer>ve böylelikle, en iyi duruma getirmek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b4c88-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="b4c88-129">Tasarımını pratik bir yararı <xref:System.Runtime.Serialization.DataContractSerializer> daha iyi performans, yaklaşık olarak yüzde onluk daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="b4c88-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="b4c88-130">Öznitelikleri ile kullanılmak üzere <xref:System.Xml.Serialization.XmlSerializer> hangi alanların ya da türünün özelliklerini XML sıralanır ancak göstermiyor <xref:System.Runtime.Serialization.DataMemberAttribute> ile kullanılmak üzere <xref:System.Runtime.Serialization.DataContractSerializer> açıkça hangi alanların ya da özellikleri seri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="b4c88-131">Bu nedenle, veri sözleşmeleri göndermek ve almak için bir uygulama olan verileri yapısı hakkında açık sözleşmeleri altındadır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="b4c88-132"><xref:System.Xml.Serialization.XmlSerializer> Yalnızca Genel üyeler .NET nesnesinin XML çevirebilir <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri üyeleri bu üyeler erişim değiştiricileri bağımsız olarak XML çevirebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="b4c88-133">XML ortak olmayan üyeler türleri serileştirmek çalışabilme gruplarındaki sonucu olarak <xref:System.Runtime.Serialization.DataContractSerializer> çeşitli XML serileştirebilen .NET türleri üzerinde daha az kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="b4c88-134">Özellikle, XML türleri gibi içine çevirebilir <xref:System.Collections.Hashtable> uygulayan <xref:System.Collections.IDictionary> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b4c88-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="b4c88-135"><xref:System.Runtime.Serialization.DataContractSerializer> Türü tanımını değiştirin ya da bir sarmalayıcı için geliştirme gerek kalmadan XML halinde önceden var olan tüm .NET türünün örneklerini serileştirmek çok daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="b4c88-136">Başka bir sonucu <xref:System.Runtime.Serialization.DataContractSerializer> bir türün genel olmayan üyeleri erişebildiklerinden olduğundan tam güven gerektirir ancak <xref:System.Xml.Serialization.XmlSerializer> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b4c88-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="b4c88-137">Tam güven kodu erişim izni altında kod yürütüyor kimlik bilgileri kullanılarak erişilebilir bir makine tüm kaynaklara tam erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="b4c88-138">Bu seçenek tam olarak güvenilen kod makinenizde tüm kaynakları erişir gibi dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="b4c88-139"><xref:System.Runtime.Serialization.DataContractSerializer> Sürüm oluşturma için bazı destek içerir:</span><span class="sxs-lookup"><span data-stu-id="b4c88-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="b4c88-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> false değeri, böylece uygulamaların olmasını sözleşme daha yeni sürümü ile izin verecek şekilde bir veri Sözleşmesi'nın önceki sürümlerinde, mevcut olmayan yeni sürümlerine eklenen üyeler için atanabilir özelliği önceki sürümlerde işlemek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4c88-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="b4c88-141">Uygulayan bir veri sözleşmesi sahip <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi, bir izin verebilir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesi uygulamalarıyla daha yeni sürümlerinde sözleşme önceki sürümleriyle tanımlanan üyeleri geçirmek için.</span><span class="sxs-lookup"><span data-stu-id="b4c88-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="b4c88-142">Tüm farklılıklar, XML, öğesine rağmen <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="b4c88-143">Öznitelikleri serileştiricileri her ikisi de ile kullanmak için aşağıdaki sınıf tarafından anlamsal olarak aynı XML veri dönüştürülür <xref:System.Xml.Serialization.XmlSerializer> ve göre <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="b4c88-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-144">Windows Yazılım Geliştirme Seti (SDK) adlı bir komut satırı aracı içerir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b4c88-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b4c88-145">ASP.NET Web Hizmetleri ile kullanılan XSD.exe'nin aracı gibi Svcutil.exe XML şemasından .NET veri türlerinin tanımlarını oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="b4c88-146">Veri sözleşmeleri varsa türleridir <xref:System.Runtime.Serialization.DataContractSerializer> XML XML şeması tarafından tanımlanan biçimde yayma; Aksi halde, bunlar serileştirme kullanmak için tasarlanmıştır <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b4c88-147">Svcutil.exe de üretebilir XML Şeması veri sözleşmelerinden kullanarak kendi `dataContractOnly` geçin.</span><span class="sxs-lookup"><span data-stu-id="b4c88-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4c88-148">Kullanım ASP.NET Web Hizmetleri olsa da <xref:System.Xml.Serialization.XmlSerializer>ve WCF ASP.NET uyumluluk modu yapar ASP.NET Web Hizmetleri davranışını taklit eden WCF hizmetleri, ASP.NET uyumluluğu seçeneği kullanılarak birine kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b4c88-149">Bir kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetleri ile.</span><span class="sxs-lookup"><span data-stu-id="b4c88-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="b4c88-150">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="b4c88-150">Service Development</span></span>  
 <span data-ttu-id="b4c88-151">ASP.NET kullanarak bir hizmeti geliştirmek için onu eklemek için her zamanki <xref:System.Web.Services.WebService> bir sınıfa öznitelik ve <xref:System.Web.Services.WebMethodAttribute> hizmetinin operations olacak o sınıfın yöntemlerden herhangi birini için:</span><span class="sxs-lookup"><span data-stu-id="b4c88-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-152">ASP.NET 2.0 sunulan öznitelik ekleme seçeneğiniz <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> bir arabirime yerine bir sınıf ve arabirimini uygulayan bir sınıf yazmak için:</span><span class="sxs-lookup"><span data-stu-id="b4c88-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-153">Bu seçeneği kullanarak olduğundan tercih edilen, olması için arabirimle <xref:System.Web.Services.WebService> özniteliği oluşturduğunu aynı sözleşme farklı şekillerde uygulayabilir çeşitli sınıflarıyla yeniden hizmeti tarafından gerçekleştirilen işlemler için bir sözleşmede.</span><span class="sxs-lookup"><span data-stu-id="b4c88-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="b4c88-154">Bir WCF hizmeti bir veya daha fazla WCF uç noktaları tanımlayarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="b4c88-155">Bir uç nokta bir adresi, bağlama ve hizmet sözleşmesini tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="b4c88-156">Hizmet bulunduğu adresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-156">The address defines where the service is located.</span></span> <span data-ttu-id="b4c88-157">Bağlama hizmetiyle iletişim kurma belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="b4c88-158">Hizmet Sözleşmesi Hizmet gerçekleştirebileceğiniz işlemler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-158">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="b4c88-159">Hizmet sözleşmesi genellikle ilk olarak, ekleyerek tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> bir arabirim için:</span><span class="sxs-lookup"><span data-stu-id="b4c88-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="b4c88-160"><xref:System.ServiceModel.ServiceContractAttribute> Arabirimi bir WCF hizmet sözleşmesini tanımlayan belirtir ve <xref:System.ServiceModel.OperationContractAttribute> , varsa, arabirim yöntemleri hizmet sözleşmesinin işlemleri tanımlayan gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="b4c88-161">Bir hizmet sözleşmesini tanımlandıktan sonra hizmet sözleşmesi tanımlandığı arabirimini uygulayan sınıf sağlayarak bir sınıfta uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b4c88-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="b4c88-162">Bir hizmet sözleşmesini uygulayan bir sınıf içinde WCF hizmet olarak yazmak için denir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>  
  
 <span data-ttu-id="b4c88-163">Bir adresi ve bir bağlama hizmet türü ile ilişkilendirmek için sonraki adım olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="b4c88-164">Genellikle bir yapılandırma dosyasında, dosyanın doğrudan düzenleyerek veya WCF ile sağlanan yapılandırma Düzenleyicisi kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="b4c88-165">Bir yapılandırma dosyası bir örneği burada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-165">Here is an example of a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b4c88-166">Bağlama uygulamayla iletişim kurmak için protokol kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="b4c88-167">Aşağıdaki tabloda ortak seçenekleri temsil eden sistem tarafından sağlanan bağlamalar listeler.</span><span class="sxs-lookup"><span data-stu-id="b4c88-167">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="b4c88-168">Ad</span><span class="sxs-lookup"><span data-stu-id="b4c88-168">Name</span></span>|<span data-ttu-id="b4c88-169">Amaç</span><span class="sxs-lookup"><span data-stu-id="b4c88-169">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="b4c88-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-170">BasicHttpBinding</span></span>|<span data-ttu-id="b4c88-171">Web Hizmetleri ve WS-BasicProfile 1.1 ve temel güvenlik profili 1.0 destekleyen istemciler ile birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="b4c88-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="b4c88-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-172">WSHttpBinding</span></span>|<span data-ttu-id="b4c88-173">Web Hizmetleri ve desteği WS - istemcileri ile birlikte çalışabilirlik \* HTTP üzerinden iletişim kuralları.</span><span class="sxs-lookup"><span data-stu-id="b4c88-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|  
|<span data-ttu-id="b4c88-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-174">WSDualHttpBinding</span></span>|<span data-ttu-id="b4c88-175">Çift yönlü HTTP iletişimi, ilk ileti alıcısı doğrudan ilk göndereni yanıtlamak değil, ancak yanıt herhangi bir sayıda in conformity with WS - HTTP kullanarak bir süre boyunca ileten \* protokoller.</span><span class="sxs-lookup"><span data-stu-id="b4c88-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|  
|<span data-ttu-id="b4c88-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-176">WSFederationBinding</span></span>|<span data-ttu-id="b4c88-177">Bir hizmeti kaynaklarına erişimi denetlenebilir, HTTP iletişimi açıkça tanımlanmış kimlik bilgisi sağlayıcısı tarafından verilen kimlik bilgileri temel.</span><span class="sxs-lookup"><span data-stu-id="b4c88-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="b4c88-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-178">NetTcpBinding</span></span>|<span data-ttu-id="b4c88-179">Bir ağ üzerinden WCF yazılım varlıklar arasındaki iletişimi güvenli, güvenilir ve yüksek performans.</span><span class="sxs-lookup"><span data-stu-id="b4c88-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|  
|<span data-ttu-id="b4c88-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="b4c88-181">Aynı makine üzerinde WCF yazılım varlıklar arasındaki iletişimi güvenli, güvenilir ve yüksek performans.</span><span class="sxs-lookup"><span data-stu-id="b4c88-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|  
|<span data-ttu-id="b4c88-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-182">NetMsmqBinding</span></span>|<span data-ttu-id="b4c88-183">MSMQ kullanarak WCF yazılım varlıklar arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="b4c88-183">Communication between WCF software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="b4c88-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="b4c88-185">Bir WCF yazılım varlık ve MSMQ kullanarak başka bir yazılım varlık arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="b4c88-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="b4c88-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="b4c88-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="b4c88-187">Windows Eşler arası ağ iletişimi kullanarak WCF yazılım varlıklar arasındaki iletişim.</span><span class="sxs-lookup"><span data-stu-id="b4c88-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="b4c88-188">Sistem tarafından sağlanan bağlama <xref:System.ServiceModel.BasicHttpBinding>, ASP.NET Web Hizmetleri tarafından desteklenen protokolleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="b4c88-189">Özel bağlamalar WCF uygulamaları için kolayca tekil protokollerin uygulamak için WCF kullanır bağlama öğe sınıfları koleksiyon olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="b4c88-190">Yeni bağlama öğeleri, ek protokoller temsil etmek için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-190">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="b4c88-191">Hizmet türleri iç davranışını ailesi davranışları adlı sınıfları, özellikleri kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="b4c88-192">Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıfı hizmet türü birden çok iş parçacıklı olduğunu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="b4c88-193">Bazı davranışları ister <xref:System.ServiceModel.ServiceBehaviorAttribute>, öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="b4c88-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="b4c88-194">Diğer yöneticiler ayarlamak için istediğiniz özelliklere sahip olanları uygulama yapılandırmasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="b4c88-195">Hizmet türlerini programlama sık kullanılan olarak yapılan <xref:System.ServiceModel.OperationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b4c88-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="b4c88-196">Kendi statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği bir işlem çalıştığından bağlamı ile ilgili bilgilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="b4c88-197"><xref:System.ServiceModel.OperationContext> her ikisi de benzer <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="b4c88-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="b4c88-198">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b4c88-198">Hosting</span></span>  
 <span data-ttu-id="b4c88-199">ASP.NET Web Hizmetleri, bir sınıf kitaplığı derlemeye derlenir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="b4c88-200">Hizmet dosyası adlı bir dosya uzantısı .asmx sahip ve içeren koşuluyla olan bir `@ WebService` hizmeti ve onu bulunduğu derleme kodunu içeren sınıf tanımlar yönergesi.</span><span class="sxs-lookup"><span data-stu-id="b4c88-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="b4c88-201">Hizmet dosyası, ASP.NET uygulama kökü Internet Information Services (IIS) kopyalanır ve derleme o uygulama kökü \bin alt kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="b4c88-202">Uygulama sonra Tekdüzen Kaynak Konum Belirleyicisi (URL)'uygulama kök hizmet dosyasının kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 <span data-ttu-id="b4c88-203">WCF hizmetleri taşımalarına IIS 5.1 veya 6.0, Windows İşlem Etkinleştirme Hizmeti (IIS 7. 0'da, bir parçası olarak sağlanan WAS) içinde ve herhangi bir .NET uygulama içinde barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="b4c88-204">IIS 5.1 veya 6.0 hizmetinde barındırmak için hizmet iletişimleri Aktarım Protokolü olarak HTTP kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="b4c88-205">Bir hizmet WAS veya IIS 5.1, 6.0 içinde barındırmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="b4c88-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="b4c88-206">Sınıf kitaplığı derlemesini hizmet türü derleyin.</span><span class="sxs-lookup"><span data-stu-id="b4c88-206">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="b4c88-207">.Svc uzantısına sahip bir hizmet dosyası oluşturma bir `@ ServiceHost` yönergesi hizmet türünü tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="b4c88-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="b4c88-208">Bir sanal dizin ve bu sanal dizine \bin alt derlemeye hizmet dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b4c88-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="b4c88-209">Yapılandırma dosyasını sanal dizine kopyalayın ve Web.config adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b4c88-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="b4c88-210">Uygulama daha sonra uygulama kökü hizmet dosyasında URL'yi kullanarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-210">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="b4c88-211">.NET uygulaması içindeki bir WCF Hizmeti barındırma için uygulama tarafından başvurulan bir sınıf kitaplığı derlemesini hizmet türü derlemek ve ana bilgisayar hizmeti kullanarak uygulamaya program <xref:System.ServiceModel.ServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b4c88-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="b4c88-212">Gerekli temel programlama örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b4c88-212">The following is an example of the basic programming required:</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-213">Bu örnek, bir veya daha fazla aktarım protokolleri için adresleri oluşturma işlemi belirtilen nasıl gösterir bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b4c88-214">Bu adresler temel adresleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-214">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="b4c88-215">Herhangi bir WCF Hizmeti uç noktası için sağlanan adresi, bir taban adresi uç noktanın konağının göreli bir adrestir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="b4c88-216">Konağın her iletişim Aktarım Protokolü için bir taban adresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="b4c88-217">Önceki yapılandırma dosyasında örnek yapılandırmasında <xref:System.ServiceModel.BasicHttpBinding> HTTP uç noktası kullanımları Aktarım Protokolü olarak şekilde uç noktası adresi seçili `EchoService`, ana bilgisayarın HTTP temel göre adresidir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="b4c88-218">Ana bilgisayarın söz konusu olduğunda önceki örnekte, HTTP temel adresi olduğunu http://www.contoso.com:8000/.</span><span class="sxs-lookup"><span data-stu-id="b4c88-218">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="b4c88-219">IIS ya da WAS içinde barındırılan bir hizmet için taban adresi hizmetin hizmet dosyasının URL'dir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="b4c88-220">IIS veya WAS ve hangi HTTP ile Aktarım Protokolü olarak yalnızca, yapılandırılmış barındırılan yalnızca hizmetlerine WCF ASP.NET uyumluluk modu seçeneğini kullanmak için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="b4c88-221">Bu seçenek açma aşağıdaki adımları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-221">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="b4c88-222">Programcı eklemelisiniz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> özniteliği için hizmet türü ve ASP.NET uyumluluk modunda izin verilen veya gerekli belirtin.</span><span class="sxs-lookup"><span data-stu-id="b4c88-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="b4c88-223">Yönetici, uygulamayı ASP.NET uyumluluğu modunu kullanacak şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
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
  
     <span data-ttu-id="b4c88-224">WCF uygulamaları, kendi hizmet dosyalarda .svc yerine .asmx uzantısı olarak kullanmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
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
  
     <span data-ttu-id="b4c88-225">Bu seçenek .asmx hizmeti dosyaları URL'lerini WCF kullanmak için bir hizmet değiştirirken kullanmak üzere yapılandırılmış istemciler değiştirmek zorunda kalmaktan kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4c88-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="b4c88-226">İstemci geliştirme</span><span class="sxs-lookup"><span data-stu-id="b4c88-226">Client Development</span></span>  
 <span data-ttu-id="b4c88-227">İstemcileri ASP.NET Web Hizmetleri için giriş olarak .asmx dosyanın URL'sini sağlar WSDL.exe komut satırı aracı kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b4c88-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="b4c88-228">WCF tarafından sağlanan karşılık gelen bir araçtır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b4c88-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b4c88-229">Hizmet sözleşmesi tanımını ve bir WCF istemcisi sınıfının tanımını kod modülüyle oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4c88-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="b4c88-230">Ayrıca, adresi ve hizmet bağlama ile bir yapılandırma dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4c88-230">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="b4c88-231">Uzak Hizmet istemcisi programlama göre zaman uyumsuz bir desen program genellikle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="b4c88-232">Her zaman WSDL.exe aracı tarafından oluşturulan kodu hem bir zaman uyumlu ve zaman uyumsuz desen varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="b4c88-233">Tarafından oluşturulan kodu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) için ya da Desen belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4c88-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="b4c88-234">Bu, varsayılan olarak zaman uyumlu desenini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="b4c88-235">Aracı ile yürütülürse `/async` geçiş için zaman uyumsuz desen oluşturulan kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="b4c88-236">ASP tarafından oluşturulan WCF istemci sınıfları adlandıran garantisi yoktur. NET'in WSDL.exe aracı, varsayılan olarak, WCF istemci sınıfları Svcutil.exe aracı tarafından oluşturulan adlarında eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="b4c88-237">Özellikle, sınıf özelliklerini adlarını sahip kullanılarak serileştirilmesi <xref:System.Xml.Serialization.XmlSerializer> varsayılan olarak, WSDL.exe aracıyla geçerli olmadığı Svcutil.exe aracı tarafından oluşturulan kodu soneki özelliği verilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="b4c88-238">İleti gösterimi</span><span class="sxs-lookup"><span data-stu-id="b4c88-238">Message Representation</span></span>  
 <span data-ttu-id="b4c88-239">Gönderilen ve ASP.NET Web Hizmetleri tarafından alınan SOAP iletilerine üstbilgileri özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="b4c88-240">Öğesinden türetilmiş bir sınıf <xref:System.Web.Services.Protocols.SoapHeader> üstbilgi yapısını tanımlamak için ve ardından <xref:System.Web.Services.Protocols.SoapHeaderAttribute> üstbilgi varlığını göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-241">WCF öznitelikleri sağlar <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ve <xref:System.ServiceModel.MessageBodyMemberAttribute> hizmeti tarafından gönderilen ve alınan SOAP iletilerine yapısını tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="b4c88-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-242">İletileri yapısı bir ASP.NET Web hizmeti kodu tarafından kapsanan ancak bu söz dizimini iletileri yapısını açık bir temsili üretir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="b4c88-243">Ayrıca, ASP.NET sözdiziminde ileti üstbilgilerini hizmet özellikleri olarak gibi gösterilir `ProtocolHeader` özelliği önceki örnekte, iletilerin özelliklerini daha doğru bir şekilde gösterilen WCF sözdiziminde ise.</span><span class="sxs-lookup"><span data-stu-id="b4c88-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="b4c88-244">Ayrıca, WCF uç noktaları yapılandırma için eklenecek ileti üstbilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>  
  
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
  
 <span data-ttu-id="b4c88-245">Seçeneği, istemci veya hizmet için kod infrastructural protokol üstbilgisinde herhangi bir referans önlemek sağlar: üst uç nokta nasıl yapılandırıldığını nedeniyle iletileri eklenir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="b4c88-246">Hizmet Açıklaması</span><span class="sxs-lookup"><span data-stu-id="b4c88-246">Service Description</span></span>  
 <span data-ttu-id="b4c88-247">Bir HTTP GET isteği bir ASP.NET Web hizmeti .asmx dosyası için WSDL sorgu ile verme hizmet açıklamak için WSDL oluşturmak ASP.NET neden olur.</span><span class="sxs-lookup"><span data-stu-id="b4c88-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="b4c88-248">Döndürür WSDL isteğine yanıt olarak.</span><span class="sxs-lookup"><span data-stu-id="b4c88-248">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="b4c88-249">ASP.NET 2.0 yaptığı bir hizmeti Web Hizmetleri birlikte işlerliği kuruluşun temel Profil 1.1 ile uyumlu olduğunu doğrulamak olası (WS-ı) ve hizmet WSDL uyumlu olduğunu talep eklemek için.</span><span class="sxs-lookup"><span data-stu-id="b4c88-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="b4c88-250">Diğer bir deyişle Bitti'yi kullanarak `ConformsTo` ve `EmitConformanceClaims` parametrelerinin <xref:System.Web.Services.WebServiceBindingAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b4c88-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="b4c88-251">Bir hizmet için ASP.NET oluşturur WSDL özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="b4c88-252">Özelleştirmeleri, türetilmiş bir sınıf oluşturarak yapılır <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> WSDL öğeler eklemek için.</span><span class="sxs-lookup"><span data-stu-id="b4c88-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="b4c88-253">IIS 51 içinde barındırılan bir HTTP uç noktası ile bir WCF hizmeti .svc dosyası için WSDL sorgu ile bir HTTP GET isteği veren, 6.0 veya WAS hizmeti açıklamak için WSDL ile yanıtlamak WCF neden olur.</span><span class="sxs-lookup"><span data-stu-id="b4c88-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="b4c88-254">Bir .NET uygulama içinde barındırılan bir hizmete HTTP temel adresine WSDL sorgu ile bir HTTP GET isteği verme etkisi aynı de ayarlandıysa true.</span><span class="sxs-lookup"><span data-stu-id="b4c88-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="b4c88-255">Ancak, WCF ayrıca bir hizmet açıklamak için oluşturur WSDL WS-MetadataExchange isteklerine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="b4c88-256">ASP.NET Web Hizmetleri, WS-MetadataExchange istekleri için yerleşik destek yok.</span><span class="sxs-lookup"><span data-stu-id="b4c88-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="b4c88-257">WCF oluşturur WSDL kapsamlı bir şekilde özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="b4c88-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfı WSDL özelleştirmek için bazı özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="b4c88-259">WCF WSDL oluşturmak değil ancak yerine belirtilen bir URL'de statik WSDL dosyası kullanmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
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
  
## <a name="exception-handling"></a><span data-ttu-id="b4c88-260">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="b4c88-260">Exception Handling</span></span>  
 <span data-ttu-id="b4c88-261">ASP.NET Web Hizmetleri içinde işlenmeyen özel durumlar istemcilere SOAP hataları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b4c88-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="b4c88-262">Aynı zamanda açıkça örneklerini atabilirsiniz <xref:System.Web.Services.Protocols.SoapException> sınıfı ve istemciye iletilen bir SOAP hatası içeriğini daha fazla denetime sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="b4c88-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="b4c88-263">WCF hizmetlerinde işlenmeyen özel durumlar istemcilere hassas bilgilerin yanlışlıkla'nda özel durumlara yararlanılmasını önlemek için SOAP hataları olarak döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="b4c88-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="b4c88-264">Bir yapılandırma ayarı, hata ayıklama amacıyla istemcilere döndürülen özel durum işlenmemiş için sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="b4c88-265">SOAP hataları istemcilere döndürmek için genel tür örneklerini atabilirsiniz <xref:System.ServiceModel.FaultException%601>kullanarak verileri sözleşme genel tür olarak türü.</span><span class="sxs-lookup"><span data-stu-id="b4c88-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="b4c88-266">Ayrıca ekleyebileceğiniz <xref:System.ServiceModel.FaultContractAttribute> öznitelikleri bir işlem verim hataları belirtmek için işlemleri.</span><span class="sxs-lookup"><span data-stu-id="b4c88-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
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
  
 <span data-ttu-id="b4c88-267">Olası hataları sonuçlarında hizmeti WSDL içinde tanıtılan bunları yapmak, hangi hataları düşündüğünüz programcıların izin vermeden bir işlemden neden ve uygun catch deyimleri yazma.</span><span class="sxs-lookup"><span data-stu-id="b4c88-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
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
  
## <a name="state-management"></a><span data-ttu-id="b4c88-268">Durum Yönetimi</span><span class="sxs-lookup"><span data-stu-id="b4c88-268">State Management</span></span>  
 <span data-ttu-id="b4c88-269">Bir ASP.NET Web hizmeti uygulamak için kullanılan sınıfın türetildiği <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="b4c88-270">Bu durumda, sınıf kullanmak için programlanabilir <xref:System.Web.Services.WebService> sınıfı içerik özelliği erişmek için temel bir <xref:System.Web.HttpContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b4c88-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="b4c88-271"><xref:System.Web.HttpContext> Nesnesi olabilir güncelleştirme ve uygulama özelliğini kullanarak uygulama durum bilgilerini almak için kullanılan ve güncelleştirmek ve onun oturum özelliğini kullanarak oturum durumu bilgilerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="b4c88-272">ASP.NET, burada oturum durum bilgisi oturum özelliği kullanılarak önemli ölçüde denetim sağlar <xref:System.Web.HttpContext> gerçekten depolanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="b4c88-273">Tanımlama bilgileri, bir veritabanı, geçerli sunucunun bellek veya atanmış bir sunucu bellek depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="b4c88-274">Seçimi hizmetin yapılandırma dosyasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-274">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="b4c88-275">WCF genişletilebilen nesneler için durum yönetimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="b4c88-276">Genişletilebilir nesneleridir uygulayan nesneler <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="b4c88-277">En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="b4c88-278">`ServiceHostBase` tüm hizmet örneklerinin yazdığı aynı konakta durumu erişebilir, sağlamanıza olanak tanır ancak `InstanceContext` içinde bir hizmet türü'nın aynı örneğini çalıştıran herhangi bir kod tarafından erişilebilecek durumu korumanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="b4c88-279">Burada, hizmet türü `TradingSystem`, sahip bir <xref:System.ServiceModel.ServiceBehaviorAttribute> belirtir aynı WCF istemci örneğinden tüm çağrıları hizmet türü'nın aynı örneğinin yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="b4c88-280">Sınıf `DealData`, bir hizmet türünün aynı örneğinde çalışan herhangi bir kod tarafından erişilebilecek bir durum tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="b4c88-281">Hizmet sözleşmesi işlemlerden birini uygulayan hizmet türüne ilişkin kodda bir `DealData` durum nesnesi geçerli hizmet türü örneği durumuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="b4c88-282">Bu durum nesnesi alınır ve başka bir hizmet sözleşmenin işlemleri uygulayan kod tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="b4c88-283">ASP.NET üzerinde denetim sağlar ancak burada bilgilerinde durum <xref:System.Web.HttpContext> gerçekten sınıfı depolanır, WCF, en az ilk sürümünde genişletilebilen nesneler depolandığı üzerinden hiçbir denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="b4c88-284">Bir WCF hizmetini ASP.NET uyumluluk modu seçmek için en iyi neden meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="b4c88-285">Yapılandırılabilir durum yönetimi kesinlik temelli sonra ASP.NET uyumluluk modu kullanmama sağlar, özelliklerini kullanabilmeniz <xref:System.Web.HttpContext> sınıfı tam olarak ASP.NET ve yapılandırmak için kullanıldıkları haliyle burada durum kullanılarakyönetilenbilgisi<xref:System.Web.HttpContext> sınıfı depolanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="b4c88-286">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b4c88-286">Security</span></span>  
 <span data-ttu-id="b4c88-287">ASP.NET Web Hizmetleri güvenli hale getirme seçenekleri herhangi bir IIS uygulama güvenliğini sağlamak için olanlardır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="b4c88-288">WCF uygulamalar yalnızca IIS içinde aynı zamanda herhangi bir .NET yürütülebilir dosya içinde barındırılan olduğundan, WCF uygulamalarının güvenliğini sağlama seçeneklerini IIS tesis bağımsız yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="b4c88-289">Ancak, ASP.NET Web Hizmetleri için sağlanan özellikleri de ASP.NET uyumluluk modunda çalışan WCF hizmetleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="b4c88-290">Güvenlik: kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b4c88-290">Security: Authentication</span></span>  
 <span data-ttu-id="b4c88-291">IIS olarak seçebileceğiniz Anonim erişim veya kimlik doğrulama modları çeşitli uygulamalara erişimi denetleme olanakları sağlar: Windows kimlik doğrulaması, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="b4c88-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="b4c88-292">Windows kimlik doğrulaması seçeneği, ASP.NET Web Hizmetleri erişimi denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="b4c88-293">Ancak, WCF uygulamaları IIS içinde barındırıldığında, IIS kimlik doğrulamanın diğer çeşitli seçenekler arasından Windows kimlik doğrulamasını destekleyen WCF kendisi tarafından yönetilecek şekilde uygulama anonim erişime izin vermek için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="b4c88-294">Yerleşik diğer seçenekler, kullanıcı adı belirteçleri, X.509 sertifikaları, SAML belirteçleri ve CardSpace kart içerir, ancak özel kimlik doğrulama mekanizmaları de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="b4c88-295">Güvenlik: kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="b4c88-295">Security: Impersonation</span></span>  
 <span data-ttu-id="b4c88-296">ASP.NET kimlik öğesi, bir ASP.NET Web hizmeti belirli bir kullanıcının kimliğine bürünmek için yapılabilir veya hangi kullanıcının kimlik bilgilerinin geçerli istekle sağlanan sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="b4c88-297">Bu öğe, kimliğe bürünme ASP.NET uyumluluk modunda çalışan WCF uygulamalarını yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="b4c88-298">WCF yapılandırma sistemi kimliğine bürünmek için belirli bir kullanıcı atamak için kendi kimlik öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="b4c88-299">Ayrıca, WCF istemcileri ve Hizmetleri bağımsız olarak kimliğe bürünme için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="b4c88-300">İstemciler, istekleri aktarırken geçerli kullanıcının kimliğine bürünmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="b4c88-301">Hizmet işlemleri hangi kullanıcının kimlik bilgilerinin geçerli istekle sağlanan kimliğine bürünmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="b4c88-302">Güvenlik: Erişim denetimi listeleri kullanarak Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="b4c88-302">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="b4c88-303">Erişim denetim listeleri (ACL'ler) .asmx dosyalara erişimi kısıtlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="b4c88-304">Ancak, WCF .svc dosyalarını ACL'lerin dışında ASP.NET uyumluluk modunda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="b4c88-305">Güvenlik: Rol tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="b4c88-305">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="b4c88-306">IIS Windows kimlik doğrulaması seçeneği birlikte ASP.NET yapılandırma dil tarafından sağlanan yetkilendirme öğesi ile kullanıcılara atanmış olan Windows gruplarını temel alan ASP.NET Web Hizmetleri için rol tabanlı yetkilendirme kolaylaştırmak için kullanılabilir .</span><span class="sxs-lookup"><span data-stu-id="b4c88-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="b4c88-307">ASP.NET 2.0 sunulan daha genel bir rol tabanlı yetkilendirme mekanizması: rol sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="b4c88-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="b4c88-308">Rol sağlayıcıları tüm atanmış bir kullanıcı için rolleri hakkında enquiring için temel bir arabirim uygulamak, ancak farklı bir kaynaktan bu bilgileri almak nasıl her rol sağlayıcısı bilir sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="b4c88-309">ASP.NET 2.0 rol atamalarını Windows Server 2003 Yetkilendirme Yöneticisi'nden alabilirsiniz rol atamalarını bir Microsoft SQL Server veritabanı ve başka alabilen bir rol sağlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4c88-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="b4c88-310">Rol sağlayıcı mekanizması WCF uygulaması da dahil olmak üzere tüm .NET uygulamasında gerçekte ASP.NET bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="b4c88-311">WCF uygulaması için şu örnek yapılandırma nasıl bir ASP.NET rol sağlayıcıyı kullanımı yoluyla bir seçeneğe gösterilir <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
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
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="b4c88-312">Güvenlik: Talep tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="b4c88-312">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="b4c88-313">Bir WCF en önemli yeniliklerden talepleri temelinde korunan kaynaklara erişimi yetkilendirmek için kapsamlı desteğidir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="b4c88-314">Talep türü, bir hak ve bir değer, bir sürücüleri lisans, örneğin oluşur.</span><span class="sxs-lookup"><span data-stu-id="b4c88-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="b4c88-315">Biri taşıyıcı'nin doğum tarihi olan taşıyıcı hakkında talepler kümesi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="b4c88-316">Talep değeri sürücünün doğum tarihi olsa da bu talep türünü doğum tarihi, ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="b4c88-317">Bir talep taşıyıcı confers sağ taşıyıcı talebin değeri ile neler yapabileceğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="b4c88-318">Doğum tarihi sürücünün talep durumunda elinde hangisi: Doğum tarihi ancak, örneğin olamaz, sürücü sahip, üzerinde değişiklik.</span><span class="sxs-lookup"><span data-stu-id="b4c88-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="b4c88-319">Talep tabanlı yetkilendirme, rol talep türü olduğundan rol tabanlı bir yetkilendirme barındırır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="b4c88-320">Talep tabanlı yetkilendirme gerekliliklerini işlemin ve bu karşılaştırma sonucunu bağlı olarak talepler kümesi karşılaştırma vererek ya da işlemi erişimi reddetme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="b4c88-321">WCF ' bir değer atayarak talep tabanlı yetkilendirme, bir kez yeniden çalıştırmak için bir sınıf belirtebilirsiniz `ServiceAuthorizationManager` özelliği <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b4c88-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="b4c88-322">Talep tabanlı yetkilendirme çalıştırmak için kullanılan sınıfları öğesinden türetilmelidir <xref:System.ServiceModel.ServiceAuthorizationManager>, geçersiz kılmak için yalnızca bir yöntemi olan `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="b4c88-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="b4c88-323">WCF hizmet işlemini çağrılır ve sağlar bu yöntemi çağırır bir <xref:System.ServiceModel.OperationContext> kullanıcı talebini sahip nesne, kendi `ServiceSecurityContext.AuthorizationContext` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b4c88-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="b4c88-324">WCF mu hangi güvenlik belirteci kullanıcı hakkında talepleri atayarak iş bırakır kimlik doğrulaması için sağlanan kullanıcı bu talep ilgili işlem için yeterli olup olmadığını değerlendirmek, görev.</span><span class="sxs-lookup"><span data-stu-id="b4c88-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="b4c88-325">Kimlik doğrulama mekanizması tamamen bağımsız talep tabanlı yetkilendirme kodu kolaylaştırır WCF güvenlik herhangi bir tür otomatik olarak talep derler yüksek oranda önemli bir yenilik belirteci olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="b4c88-326">Bunun aksine, ACL'ler ya da roller ASP.NET kullanarak yetkilendirmeyi yakından Windows kimlik doğrulaması olarak bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="b4c88-327">Güvenlik: gizlilik</span><span class="sxs-lookup"><span data-stu-id="b4c88-327">Security: Confidentiality</span></span>  
 <span data-ttu-id="b4c88-328">ASP.NET Web Hizmetleri ile değiştirilen iletilerin gizliliğini aktarım düzeyinde uygulamayı IIS içinde Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak güvence altına alınabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="b4c88-329">Aynı içinde IIS barındırılan WCF uygulamalar için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="b4c88-330">Ancak, dışında IIS barındırılan WCF uygulamaları güvenli aktarım protokolünü kullanmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="b4c88-331">Daha da önemlisi, WCF uygulamaları, bunlar, WS-güvenlik protokolünü kullanarak taşınacağını önce iletileri güvenli hale getirmek için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="b4c88-332">WS güvenliği kullanarak ileti gövdesi güvenliğini sağlama ilkemiz aracılar son hedefine ulaşmadan önce iletilmesi izin verir.</span><span class="sxs-lookup"><span data-stu-id="b4c88-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="b4c88-333">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="b4c88-333">Globalization</span></span>  
 <span data-ttu-id="b4c88-334">ASP.NET yapılandırma dil tek tek Hizmetleri için kültür belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="b4c88-335">WCF ASP.NET uyumluluk modunda dışında bu yapılandırma ayarını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="b4c88-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="b4c88-336">ASP.NET uyumluluğu modunu kullanmayan bir WCF Hizmeti yerelleştirme için hizmet türü kültüre özgü derlemeler içine derleyin ve her kültüre özgü derlemesi için ayrı kültüre özgü uç noktalar vardır.</span><span class="sxs-lookup"><span data-stu-id="b4c88-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c88-337">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4c88-337">See Also</span></span>  
 [<span data-ttu-id="b4c88-338">ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="b4c88-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
