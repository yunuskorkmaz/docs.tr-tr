---
title: Serileştirme ve Meta Veriler
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 1805b6ca06d584237303d1366222419da3e8b9ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128117"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="a5aec-102">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="a5aec-102">Serialization and Metadata</span></span>

<span data-ttu-id="a5aec-103">Uygulamanız nesneleri serileştirir ve onları yeniden ayırır, gerekli meta verilerin çalışma zamanında mevcut olduğundan emin olmak için çalışma zamanı yönergeleri (. RD. xml) dosyasına girişler eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aec-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="a5aec-104">Serileştiricilerin iki kategorisi vardır ve her biri çalışma zamanı yönergeleri dosyasında farklı işleme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a5aec-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="a5aec-105">Yansıma tabanlı üçüncü taraf serileştiriciler.</span><span class="sxs-lookup"><span data-stu-id="a5aec-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="a5aec-106">Bunlar, çalışma zamanı yönergeleri dosyasında değişiklik yapılmasını gerektirir ve sonraki bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a5aec-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="a5aec-107">.NET Framework sınıfı kitaplığında yansıma tabanlı olmayan serileştiriciler bulundu.</span><span class="sxs-lookup"><span data-stu-id="a5aec-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="a5aec-108">Bunlar, çalışma zamanı yönergeleri dosyasında değişiklikler yapılmasını gerektirebilir ve [Microsoft serileştiriciler](#Microsoft) bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a5aec-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="a5aec-109">Üçüncü taraf serileştiriciler</span><span class="sxs-lookup"><span data-stu-id="a5aec-109">Third-party serializers</span></span>

 <span data-ttu-id="a5aec-110">Newtonsoft. JSON dahil olmak üzere üçüncü bölümden oluşan serileştiriciler, genellikle yansıma tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="a5aec-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="a5aec-111">Seri hale getirilmiş verilerin ikili büyük nesne (BLOB) verildiğinde, verilerdeki alanlar, hedef türdeki alanlara ada göre bakılarak somut bir türe atanır.</span><span class="sxs-lookup"><span data-stu-id="a5aec-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="a5aec-112">Bu kitaplıkların kullanılması en azından, bir `List<Type>` koleksiyonunda serileştirmek veya seri durumdan çıkarmak istediğiniz her bir <xref:System.Type> nesnesi için [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumlarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a5aec-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="a5aec-113">Bu serileştiriciler için eksik meta verilerin neden olduğu sorunları ele almanın en kolay yolu, tek bir ad alanı (örneğin, `App.Models`) altında serileştirme içinde kullanılacak türleri toplamaktır ve buna bir `Serialize` meta veri yönergesi uygular:</span><span class="sxs-lookup"><span data-stu-id="a5aec-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="a5aec-114">Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [\<ad uzayı > öğesi](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a5aec-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="a5aec-115">Microsoft serileştiriciler</span><span class="sxs-lookup"><span data-stu-id="a5aec-115">Microsoft serializers</span></span>

 <span data-ttu-id="a5aec-116"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları yansımayla güvenmese de, seri hale getirilecek veya seri durumdan çıkarılacak nesne temel alınarak kodun oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a5aec-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="a5aec-117">Her seri hale getirici için aşırı yüklenmiş oluşturucular, seri hale getirilecek veya seri durumdan çıkarılacak türü belirten bir <xref:System.Type> parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="a5aec-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="a5aec-118">Kodunuzda bu tür bir sonraki iki bölümde anlatıldığı gibi uygulamanız gereken eylemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5aec-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="a5aec-119">oluşturucuda kullanılan typeof</span><span class="sxs-lookup"><span data-stu-id="a5aec-119">typeof used in the constructor</span></span>

 <span data-ttu-id="a5aec-120">Bu serileştirme sınıflarının bir oluşturucusunu çağırır ve yöntem çağrısına C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini eklerseniz, **ek bir iş yapmanız**gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a5aec-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="a5aec-121">Örneğin, bir serileştirme sınıfı oluşturucusuna yapılan aşağıdaki çağrıların her birinde, oluşturucuya geçirilen ifadenin bir parçası olarak `typeof` anahtar sözcüğü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5aec-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="a5aec-122">.NET Native derleyici bu kodu otomatik olarak işleymeyecektir.</span><span class="sxs-lookup"><span data-stu-id="a5aec-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="a5aec-123">Oluşturucu dışında kullanılan typeof</span><span class="sxs-lookup"><span data-stu-id="a5aec-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="a5aec-124">Bu serileştirme sınıflarının bir oluşturucusunu çağırır ve aşağıdaki kodda olduğu gibi oluşturucunun C# <xref:System.Type> parametresine sağlanan ifadenin dışında [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsanız, .NET Native derleyicisi türü çözemez:</span><span class="sxs-lookup"><span data-stu-id="a5aec-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="a5aec-125">Bu durumda, aşağıdaki gibi bir giriş ekleyerek çalışma zamanı yönergeleri dosyasında türü belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a5aec-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="a5aec-126">Benzer şekilde, aşağıdaki kodda olduğu gibi, <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> gibi bir Oluşturucu çağırırsanız ve seri hale getirmek için ek <xref:System.Type> nesne dizisi sağlarsanız, .NET Native derleyicisi bu türleri çözümleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="a5aec-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="a5aec-127">Her tür için aşağıdaki gibi girdileri çalışma zamanı yönergeleri dosyasına eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a5aec-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="a5aec-128">Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz. [\<türü > öğesi](type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a5aec-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5aec-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5aec-129">See also</span></span>

- [<span data-ttu-id="a5aec-130">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a5aec-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a5aec-131">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="a5aec-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="a5aec-132">\<türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="a5aec-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="a5aec-133">\<ad alanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="a5aec-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
