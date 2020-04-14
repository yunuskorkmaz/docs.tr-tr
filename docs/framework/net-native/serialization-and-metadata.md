---
title: Serileştirme ve Meta Veriler
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 7c6fe241fbf92f52abfa0eb66c37bff4d227b4e5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241925"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="70350-102">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="70350-102">Serialization and Metadata</span></span>

<span data-ttu-id="70350-103">Uygulamanız nesneleri seri hale getirebilir ve deserialize ederse, gerekli meta verilerin çalışma zamanında bulunduğundan emin olmak için çalışma zamanı yönergelerinize (.rd.xml) giriş eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="70350-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="70350-104">İki serializers kategorisi vardır ve her biri çalışma zamanı yönergeleri dosyanızda farklı işleme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="70350-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="70350-105">Yansıma tabanlı üçüncü taraf serileştiriciler.</span><span class="sxs-lookup"><span data-stu-id="70350-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="70350-106">Bunlar çalışma zamanı yönergeleri dosyanızda değişiklik gerektirir ve bir sonraki bölümde tartışılır.</span><span class="sxs-lookup"><span data-stu-id="70350-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="70350-107">.NET Framework sınıf kitaplığında bulunan yansıma tabanlı olmayan serializers.</span><span class="sxs-lookup"><span data-stu-id="70350-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="70350-108">Bunlar çalışma zamanı yönergeleri dosyanızda değişiklik yapılmasını gerektirebilir ve [Microsoft serializers](#Microsoft) bölümünde tartışılır.</span><span class="sxs-lookup"><span data-stu-id="70350-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="70350-109">Üçüncü taraf serileştiriciler</span><span class="sxs-lookup"><span data-stu-id="70350-109">Third-party serializers</span></span>

 <span data-ttu-id="70350-110">Newtonsoft.JSON dahil olmak üzere üçüncü bölüm serializers, genellikle yansıma tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="70350-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="70350-111">Serileştirilmiş verilerin ikili büyük nesnesi (BLOB) göz önüne alındığında, verilerdeki alanlar hedef türündeki alanlara adıyla bakarak somut bir türe atanır.</span><span class="sxs-lookup"><span data-stu-id="70350-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="70350-112">En azından, bu kitaplıkları kullanarak bir <xref:System.Type> `List<Type>` koleksiyonda seri hale getirmeye veya deserialize etmeye çalıştığınız her nesne için Eksik [MetadataException](missingmetadataexception-class-net-native.md) özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="70350-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="70350-113">Bu serileştiriciler için eksik meta verilerin neden olduğu sorunları gidermenin en kolay yolu, serileştirmede tek `App.Models`bir ad `Serialize` alanı altında (örneğin) kullanılacak türleri toplamak ve ona bir meta veri yönergesi uygulamaktır:</span><span class="sxs-lookup"><span data-stu-id="70350-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="70350-114">Örnekte kullanılan sözdizimi hakkında bilgi için Ad [ \<alanı> Öğesi'ne](namespace-element-net-native.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="70350-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="70350-115">Microsoft serializers</span><span class="sxs-lookup"><span data-stu-id="70350-115">Microsoft serializers</span></span>

 <span data-ttu-id="70350-116"><xref:System.Runtime.Serialization.DataContractSerializer>" ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> sınıflar yansımaya dayanmasa da, seri hale getirilecek veya deserialized olacak nesneye dayalı olarak oluşturulacak kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="70350-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="70350-117">Her serileştirici için aşırı yüklü yapıcılar, seri hale getirilecek veya deserialized türünü belirten bir <xref:System.Type> parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="70350-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="70350-118">Kodunuzdaki bu türü nasıl belirtdiğiniz, sonraki iki bölümde açıklanıldığı gibi, işleminizi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70350-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="70350-119">konstrüktörde kullanılan tip</span><span class="sxs-lookup"><span data-stu-id="70350-119">typeof used in the constructor</span></span>

 <span data-ttu-id="70350-120">Bu serileştirme sınıflarının bir oluşturucusu çağırır ve yöntem çağrısına C# [tipi](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) işleci **eklerseniz, ek bir iş yapmanız gerekmez.**</span><span class="sxs-lookup"><span data-stu-id="70350-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="70350-121">Örneğin, aşağıdaki çağrıların her birinde bir serileştirme sınıfı `typeof` oluşturucuya, anahtar kelime oluşturucuya geçirilen ifadenin bir parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70350-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="70350-122">.NET Native derleyicisi bu kodu otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="70350-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="70350-123">yapıcı dışında kullanılan tip</span><span class="sxs-lookup"><span data-stu-id="70350-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="70350-124">Bu serileştirme sınıflarının oluşturucusu çağırır ve [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) aşağıdaki kodda olduğu gibi,.NET Native <xref:System.Type> derleyicisi aşağıdaki kodda olduğu gibi, oluşturucunun parametresine verilen ifadenin dışında C# tipi işleci kullanırsanız, .NET Native derleyicisi türü çözemez:</span><span class="sxs-lookup"><span data-stu-id="70350-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="70350-125">Bu durumda, aşağıdaki gibi bir giriş ekleyerek çalışma zamanı yönergeleri dosyasındaki türü belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="70350-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="70350-126">Benzer şekilde, aşağıdaki kodda olduğu <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> gibi serihale <xref:System.Type> getirmek için bir dizi ek nesne çağırır ve sağlarsanız, .NET Native derleyicisi bu türleri çözemez.</span><span class="sxs-lookup"><span data-stu-id="70350-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="70350-127">Çalışma zamanı yönergeleri dosyasına her tür için aşağıdaki gibi girişler eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="70350-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="70350-128">Örnekte kullanılan sözdizimi hakkında bilgi için, [ \<> Öğesi Türü'ne](type-element-net-native.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="70350-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70350-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70350-129">See also</span></span>

- [<span data-ttu-id="70350-130">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="70350-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="70350-131">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="70350-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="70350-132">\<> Öğesi Yazın</span><span class="sxs-lookup"><span data-stu-id="70350-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="70350-133">\<Ad Alanı> Öğesi</span><span class="sxs-lookup"><span data-stu-id="70350-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
