---
title: Serileştirme ve Meta Veriler
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f046341b1b02c3552ecf8db7d38d2a0c7bc74fba
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306363"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="6abde-102">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="6abde-102">Serialization and Metadata</span></span>

<span data-ttu-id="6abde-103">Uygulamanızı serileştirir ve nesneleri seri durumdan çıkarır, girişler için çalışma zamanı yönergeleri eklemeniz gerekebilir (. rd.xml) dosyasını gerekli meta verileri çalışma zamanında mevcut olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6abde-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="6abde-104">Seri hale getiricileri genişletme iki kategorisi vardır ve her çalışma zamanı yönergeleri dosyanızda farklı işleme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6abde-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="6abde-105">Üçüncü taraf seri hale getiricileri genişletme yansıma tabanlı.</span><span class="sxs-lookup"><span data-stu-id="6abde-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="6abde-106">Bu değişiklikler, çalışma zamanı yönergeleri dosyanıza gerektirir ve sonraki bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="6abde-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="6abde-107">Yansıma olmayan .NET Framework sınıf kitaplığında bulunan seri hale getiricileri genişletme temel.</span><span class="sxs-lookup"><span data-stu-id="6abde-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="6abde-108">Bu değişiklikler, çalışma zamanı yönergeleri dosyanıza gerektirebilir ve ele alınmıştır [Microsoft seri hale getiricileri genişletme](#Microsoft) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6abde-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="6abde-109">Üçüncü taraf seri hale getiricileri genişletme</span><span class="sxs-lookup"><span data-stu-id="6abde-109">Third-party serializers</span></span>

 <span data-ttu-id="6abde-110">Yansıma tabanlı üçüncü bölümü seri hale getiricileri genişletme Newtonsoft.JSON, dahil, normal uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6abde-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="6abde-111">Serileştirilmiş veriler ikili büyük nesne (BLOB) göz önünde bulundurulduğunda, veri alanları hedef türünün alanları ada göre arayarak somut bir türde atanır.</span><span class="sxs-lookup"><span data-stu-id="6abde-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="6abde-112">En azından bu kitaplıkları kullanarak neden [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) her biri için özel durumlar <xref:System.Type> serileştirmek veya de seri durumdan çalıştığınızda nesne bir `List<Type>` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6abde-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="6abde-113">Bu seri hale getiricileri genişletme meta veriler eksik neden sorunlarını gidermek için en kolay yolu, tek bir ad altında serileştirme sırasında kullanılan türleri toplamaktır (gibi `App.Models`) ve geçerli bir `Serialize` meta verileri yönergesine:</span><span class="sxs-lookup"><span data-stu-id="6abde-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="6abde-114">Örnekte kullanılan söz dizimi hakkında daha fazla bilgi için bkz: [ \<Namespace > öğesi](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="6abde-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="6abde-115">Microsoft seri hale getiricileri genişletme</span><span class="sxs-lookup"><span data-stu-id="6abde-115">Microsoft serializers</span></span>

 <span data-ttu-id="6abde-116">Ancak <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları yansıma kullanan değil, bunlar serileştirilecek veya seri durumdan için nesneye bağlı kod oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6abde-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="6abde-117">Her seri hale getirici için aşırı yüklü oluşturucular dahil bir <xref:System.Type> parametresi serileştirilecek veya seri durumdan türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6abde-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="6abde-118">Bu tür kodunuzda nasıl belirttiğiniz gerçekleştirmeniz gereken eylemi sonraki iki bölümde açıklandığı gibi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6abde-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="6abde-119">typeof oluşturucuda kullanılır</span><span class="sxs-lookup"><span data-stu-id="6abde-119">typeof used in the constructor</span></span>

 <span data-ttu-id="6abde-120">Bu seri hale getirme sınıfların bir oluşturucuyu çağırmak ve dahil C# [typeof](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator) işleci yöntem çağrısında **herhangi bir ek çalışma yapmak gerekmez**.</span><span class="sxs-lookup"><span data-stu-id="6abde-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="6abde-121">Örneğin, her bir seri hale getirme sınıfı oluşturucusunu aşağıdaki çağrıları içinde `typeof` anahtar sözcüğü, oluşturucuya geçirilen ifade parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6abde-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="6abde-122">.NET yerel derleyici Bu kod otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="6abde-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="6abde-123">typeof Oluşturucu dışında kullanılan</span><span class="sxs-lookup"><span data-stu-id="6abde-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="6abde-124">Bu seri hale getirme sınıfların bir oluşturucuyu çağırmak ve kullanmak C# [typeof](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator) dışında oluşturucunun sağlanan ifade işleci <xref:System.Type> parametresi, aşağıdaki kod, .NET yerel derleyici olduğu gibi tür çözümlenemiyor:</span><span class="sxs-lookup"><span data-stu-id="6abde-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="6abde-125">Bu durumda, türü çalışma zamanı yönergeleri dosyasında şunun gibi bir giriş ekleyerek belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6abde-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="6abde-126">Benzer şekilde, bir oluşturucu gibi çağırırsanız <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> ve bir dizi ek <xref:System.Type> nesneleri aşağıdaki kodda, .NET yerel derleyici bu tür çözümlenemiyor olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="6abde-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="6abde-127">Çalışma zamanı yönergeleri dosyasına girişleri her türü aşağıdaki gibi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6abde-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="6abde-128">Örnekte kullanılan söz dizimi hakkında daha fazla bilgi için bkz: [ \<türü > öğesi](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="6abde-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6abde-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6abde-129">See also</span></span>

- [<span data-ttu-id="6abde-130">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6abde-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6abde-131">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6abde-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="6abde-132">\<Türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="6abde-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="6abde-133">\<Namespace > öğesi</span><span class="sxs-lookup"><span data-stu-id="6abde-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
