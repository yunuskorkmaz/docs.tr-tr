---
title: "Serileştirme ve Meta Veriler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7216f14fb0b8da27b870fc8e66b24f6d87fcaad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="7c2a6-102">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="7c2a6-102">Serialization and Metadata</span></span>
<span data-ttu-id="7c2a6-103">Uygulamanızı serileştirir ve nesneleri seri durumdan çıkarır, çalışma zamanı yönergeleri girişleri eklemeniz gerekebilir (. rd.xml) dosyası gerekli meta veri çalışma zamanında mevcut olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="7c2a6-104">Serileştiricileri iki kategorisi vardır ve her çalışma zamanı yönergeleri dosyanızda farklı işleme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7c2a6-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
-   <span data-ttu-id="7c2a6-105">Yansıma tabanlı üçüncü taraf serileştiricileri.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="7c2a6-106">Bu çalışma zamanı yönergeleri dosyanıza değişiklikler gerektirir ve sonraki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
-   <span data-ttu-id="7c2a6-107">.NET Framework Sınıf Kitaplığı'nda bulunan serileştiricileri olmayan yansıma tabanlı.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="7c2a6-108">Bu, çalışma zamanı yönergeleri dosyanızı değişiklikler gerektirebilir ve ele alınmıştır [Microsoft serileştiricileri](#Microsoft) bölümü.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="7c2a6-109">Üçüncü taraf serileştiricileri</span><span class="sxs-lookup"><span data-stu-id="7c2a6-109">Third-party serializers</span></span>  
 <span data-ttu-id="7c2a6-110">Yansıma tabanlı üçüncü bölümü serileştiricileri Newtonsoft.JSON, dahil olmak üzere, genellikle.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="7c2a6-111">Serileştirilmiş veriler ikili büyük nesne (BLOB) göz önüne alındığında, veri alanları hedef türünün alanları ada göre arayarak somut bir türde atanır.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="7c2a6-112">Bu kitaplıklar kullanarak en az neden [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) her biri için özel durumlar <xref:System.Type> serileştirmek veya seri durumdan içinde çalıştığınızda nesne bir `List<Type>` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="7c2a6-113">Eksik meta verileri ile bu serileştiricileri için neden olduğu sorunları gidermek için en kolay yolu, tek bir ad altında serileştirmede kullanılacak türleri toplamaktır (gibi `App.Models`) ve geçerli bir `Serialize` meta verileri yönergeye:</span><span class="sxs-lookup"><span data-stu-id="7c2a6-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="7c2a6-114">Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz: [ \<Namespace > öğesi](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a6-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="7c2a6-115">Microsoft serileştiricileri</span><span class="sxs-lookup"><span data-stu-id="7c2a6-115">Microsoft serializers</span></span>  
 <span data-ttu-id="7c2a6-116">Ancak <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları yansıma bağlı değil, oluşturulacak kod serileştirilecek veya seri için seçtiğiniz nesneye bağlı duyarlar.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="7c2a6-117">Her seri hale getirici için aşırı yüklü oluşturucular içeren bir <xref:System.Type> serileştirilecek veya seri durumdan türünü belirten parametre.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="7c2a6-118">Bu tür kodunuzu nasıl belirttiğiniz gerçekleştirmesi gereken eylemi sonraki iki bölümde açıklandığı gibi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="7c2a6-119">typeof oluşturucuda kullanılır</span><span class="sxs-lookup"><span data-stu-id="7c2a6-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="7c2a6-120">Bu seri hale getirme sınıfların Oluşturucusu çağırın ve C# dahil [typeof](~/docs/csharp/language-reference/keywords/typeof.md) yöntem çağrısı bir anahtar sözcük **başka çalışma yapmak zorunda**.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="7c2a6-121">Örneğin, her bir seri hale getirme sınıf oluşturucu aşağıdaki çağrıları içinde `typeof` anahtar sözcüğü oluşturucuya geçirilen ifade parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="7c2a6-122">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici otomatik olarak bu kodu işler.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="7c2a6-123">typeof Oluşturucusu dışında kullanılan</span><span class="sxs-lookup"><span data-stu-id="7c2a6-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="7c2a6-124">Bu seri hale getirme sınıfların Oluşturucusu çağırın ve C# kullanan [typeof](~/docs/csharp/language-reference/keywords/typeof.md) anahtar sözcüğü oluşturucuya 's sağlanan ifade dışında <xref:System.Type> parametresi, aşağıdaki kod, olduğu gibi [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici olamaz türü çözümlenemedi:</span><span class="sxs-lookup"><span data-stu-id="7c2a6-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="7c2a6-125">Bu durumda, türü çalışma zamanı yönergeleri dosyasında şöyle bir giriş ekleyerek belirtmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c2a6-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="7c2a6-126">Benzer şekilde, bir oluşturucu gibi çağırırsanız <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> ve bir dizi ek sağlamak <xref:System.Type> olduğu gibi aşağıdaki kod, serileştirilecek nesneleri [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici, bu tür çözmek olamaz.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="7c2a6-127">Çalışma zamanı yönergeleri dosyasına girişleri her türü aşağıdaki gibi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c2a6-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="7c2a6-128">Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz: [ \<türü > öğesi](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a6-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2a6-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c2a6-129">See Also</span></span>  
 [<span data-ttu-id="7c2a6-130">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="7c2a6-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="7c2a6-131">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="7c2a6-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="7c2a6-132">\<Tür > öğesi</span><span class="sxs-lookup"><span data-stu-id="7c2a6-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="7c2a6-133">\<Namespace > öğesi</span><span class="sxs-lookup"><span data-stu-id="7c2a6-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
