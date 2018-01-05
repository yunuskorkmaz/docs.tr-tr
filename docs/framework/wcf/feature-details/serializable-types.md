---
title: "Seri Hale Getirilebilir Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bf272e785968f9116cea20ad0c3f40eb786d1f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="serializable-types"></a><span data-ttu-id="653d9-102">Seri Hale Getirilebilir Türler</span><span class="sxs-lookup"><span data-stu-id="653d9-102">Serializable Types</span></span>
<span data-ttu-id="653d9-103">Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> tüm herkese görünür türleri serileştirir.</span><span class="sxs-lookup"><span data-stu-id="653d9-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="653d9-104">Tüm ortak okuma/yazma özellikleri ve türünde alanlar serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="653d9-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="653d9-105">Uygulayarak varsayılan davranışı değiştirebilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri türleri ve üyeleri bu özellik, denetimi altında olmayan ve öznitelikler eklemek için değiştirilemez türlerine sahip durumlarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="653d9-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="653d9-106"><xref:System.Runtime.Serialization.DataContractSerializer> "İşaretsiz" gibi türler tanır.</span><span class="sxs-lookup"><span data-stu-id="653d9-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="653d9-107">Seri hale getirme Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="653d9-107">Serialization Defaults</span></span>  
 <span data-ttu-id="653d9-108">Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> açıkça denetlemek veya türleri ve üyeleri serileştirme özelleştirmek için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="653d9-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="653d9-109">Ayrıca, bu öznitelikler için özel alanlar uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="653d9-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="653d9-110">Ancak, bu özniteliklerle işaretlenmemiş bile türleri seri serisi ve.</span><span class="sxs-lookup"><span data-stu-id="653d9-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="653d9-111">Aşağıdaki kurallar ve özel durumlar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="653d9-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="653d9-112"><xref:System.Runtime.Serialization.DataContractSerializer> Yeni oluşturulan türlerin varsayılan özellikleri kullanarak özniteliklerini bir veri sözleşmesi türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="653d9-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="653d9-113">Tüm genel alanlar ve ortak özellikleri `get` ve `set` yöntemleri serileştirilir, uyguladığınız sürece <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> özniteliği bu üye için.</span><span class="sxs-lookup"><span data-stu-id="653d9-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="653d9-114">Seri hale getirme semantiği benzer <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="653d9-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="653d9-115">İşaretsiz türlerinde yalnızca genel tür parametreleri yok oluşturucular ile serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="653d9-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="653d9-116">Bu kural için özel durum <xref:System.Runtime.Serialization.ExtensionDataObject> ile kullanılan <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="653d9-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="653d9-117">Salt okunur alan, özellikleri olmadan bir `get` veya `set` yöntemi ve iç veya özel özelliklerle `set` veya `get` yöntemleri sıralanmış değildir.</span><span class="sxs-lookup"><span data-stu-id="653d9-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="653d9-118">Bu tür özelliklerini göz ardı edilir ve hiçbir özel durum, söz konusu olduğunda yalnızca get koleksiyonları hariç.</span><span class="sxs-lookup"><span data-stu-id="653d9-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="653d9-119"><xref:System.Xml.Serialization.XmlSerializer>öznitelikler (gibi `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, vb.) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="653d9-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="653d9-120">Geçerli <xref:System.Runtime.Serialization.DataContractAttribute> seri hale getirici belirli bir türde özniteliği, bu türün herhangi bir üye göz ardı eder <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulanır.</span><span class="sxs-lookup"><span data-stu-id="653d9-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="653d9-121"><xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Özelliği ile işaretli olmayan türleri desteklenir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="653d9-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="653d9-122">Bu desteği içeren <xref:System.Runtime.Serialization.KnownTypeAttribute> işaretsiz türlerinde özniteliği.</span><span class="sxs-lookup"><span data-stu-id="653d9-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="653d9-123">"Seri hale getirme işlemini Genel üyeler, özellikler veya alanlar için devre dışı bırakmak için", uygulamanız <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> özniteliği bu üye için.</span><span class="sxs-lookup"><span data-stu-id="653d9-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="653d9-124">Devralma</span><span class="sxs-lookup"><span data-stu-id="653d9-124">Inheritance</span></span>  
 <span data-ttu-id="653d9-125">İşaretsiz türleri (olmadan türleri <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik) bu özniteliğe sahip türlerinden devrettiği; ancak, geriye doğru izin verilmez: öznitelik türleriyle işaretsiz türlerinden devral olamaz.</span><span class="sxs-lookup"><span data-stu-id="653d9-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="653d9-126">Bu kural öncelikle'nın önceki sürümlerinde yazılan kod ile geriye dönük uyumluluk sağlamak için zorlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="653d9-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653d9-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="653d9-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="653d9-128">Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler</span><span class="sxs-lookup"><span data-stu-id="653d9-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
