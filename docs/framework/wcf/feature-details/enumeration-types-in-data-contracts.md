---
title: "Veri Sözleşmelerinde Numaralandırma Türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7989996f7ed64ba4b85ddc1ca01538ec05e99e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="a8f5e-102">Veri Sözleşmelerinde Numaralandırma Türleri</span><span class="sxs-lookup"><span data-stu-id="a8f5e-102">Enumeration Types in Data Contracts</span></span>
<span data-ttu-id="a8f5e-103">Numaralandırmalar veri sözleşmesi modelinde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-103">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="a8f5e-104">Bu konuda programlama modeli açıklayan birkaç örneklerle anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-104">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="a8f5e-105">Numaralandırma temelleri</span><span class="sxs-lookup"><span data-stu-id="a8f5e-105">Enumeration Basics</span></span>  
 <span data-ttu-id="a8f5e-106">Numaralandırma türleri veri sözleşmesi modelde kullanmak için bir yoldur uygulamak için <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik türü.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-106">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="a8f5e-107">Ardından uygulamalısınız <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği her üyesine veri sözleşmede eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-107">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="a8f5e-108">Aşağıdaki örnekte, iki sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-108">The following example shows two classes.</span></span> <span data-ttu-id="a8f5e-109">İlk numaralandırma kullanır ve ikinci numaralandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-109">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="a8f5e-110">Örneği `Car` sınıfı gönderilen ya da yalnızca alınan `condition` alan değerlerden birine ayarlanır `New`, `Used`, veya `Rental`.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-110">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="a8f5e-111">Varsa `condition` olan `Broken` veya `Stolen`, <xref:System.Runtime.Serialization.SerializationException> atılır.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-111">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="a8f5e-112">Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> özellikleri (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) numaralandırma veri sözleşmeleri için her zamanki gibi.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-112">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="a8f5e-113">Numaralandırma üye değerleri</span><span class="sxs-lookup"><span data-stu-id="a8f5e-113">Enumeration Member Values</span></span>  
 <span data-ttu-id="a8f5e-114">Genellikle veri sözleşmesi Numaralandırma üye adları, sayısal değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-114">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="a8f5e-115">Ancak, ne zaman verileri kullanarak sözleşme modeli, alma tarafı ise bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, dışarı aktarılan şema sayısal değerleri korur.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-115">However, when using the data contract model, if the receiving side is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="a8f5e-116">Bu durum kullanırken olmadığını unutmayın [XmlSerializer sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="a8f5e-116">Note that this is not the case when using the [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="a8f5e-117">Önceki örnekte, `condition` ayarlanır `Used` ve verileri seri için sonuçta elde edilen XML XML'dir `<condition>Used</condition>` ve `<condition>1</condition>`.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-117">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="a8f5e-118">Bu nedenle, aşağıdaki veri sözleşmesi veri sözleşmesi eşdeğerdir `CarConditionEnum`.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-118">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="a8f5e-119">Örneğin, kullanabileceğiniz `CarConditionEnum` Gönderen tarafında ve `CarConditionWithNumbers` alan tarafta.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-119">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="a8f5e-120">Gönderen tarafı için "1" değeri kullansa `Used` ve alma tarafı kullandığı değer "20," XML gösterimi `<condition>Used</condition>` iki tarafı için.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-120">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="a8f5e-121">Veri sözleşmesi dahil edilecek uygulamalısınız <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-121">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="a8f5e-122">İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aynı zamanda tüm numaralandırması için varsayılan değer olan bir numaralandırma için her zaman özel değeri 0 (sıfır) uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-122">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="a8f5e-123">Ancak, sıfır değeri seri hale getirilemiyor ile işaretli değilse bu özel bile <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-123">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="a8f5e-124">Bu iki özel durum vardır:</span><span class="sxs-lookup"><span data-stu-id="a8f5e-124">There are two exceptions to this:</span></span>  
  
-   <span data-ttu-id="a8f5e-125">Bayrak numaralandırmalar (Bu konunun ilerleyen bölümlerinde açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="a8f5e-125">Flag enumerations (discussed later in this topic).</span></span>  
  
-   <span data-ttu-id="a8f5e-126">Numaralandırma veri üyeleriyle <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliğini `false` (; Bu durumda sıfır değeri olan numaralandırma atlanırsa serileştirilmiş veriler).</span><span class="sxs-lookup"><span data-stu-id="a8f5e-126">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="a8f5e-127">Numaralandırma üye değerlerinin özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a8f5e-127">Customizing Enumeration Member Values</span></span>  
 <span data-ttu-id="a8f5e-128">Veri sözleşmesi parçası kullanarak form Numaralandırma üye değeri özelleştirebilirsiniz <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> özelliğinin <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-128">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="a8f5e-129">Örneğin, aşağıdaki veri sözleşmesi ayrıca veri sözleşmesi eşdeğerdir `CarConditionEnum`.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-129">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="a8f5e-130">Serileştirilmiş zaman değerini `PreviouslyOwned` XML gösterimi yok `<condition>Used</condition>`.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-130">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="a8f5e-131">Basit numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a8f5e-131">Simple Enumerations</span></span>  
 <span data-ttu-id="a8f5e-132">Ayrıca, numaralandırma türleri seri hale getirebilir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği değil uygulandı.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-132">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="a8f5e-133">Bu tür Numaralandırma türleri kabul edilir tam olarak daha önce açıklandığı gibi durumlar dışında her üye (, yok <xref:System.NonSerializedAttribute> uygulanan öznitelik) kabul edilir gibi <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-133">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="a8f5e-134">Örneğin, aşağıdaki numaralandırma önceki eşdeğer bir veri sözleşmesi örtük olarak sahip `CarConditionEnum` örnek.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-134">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="a8f5e-135">Sabit veri sözleşme adına ve ad alanı ve Numaralandırma üye değerlerinin özelleştirmek gerekmediğinde basit numaralandırmalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-135">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="a8f5e-136">Basit numaralandırmalar ile ilgili notlar</span><span class="sxs-lookup"><span data-stu-id="a8f5e-136">Notes on Simple Enumerations</span></span>  
 <span data-ttu-id="a8f5e-137">Uygulama <xref:System.Runtime.Serialization.EnumMemberAttribute> basit numaralandırmalar özniteliğine etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-137">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="a8f5e-138">Desteklemediğini fark etmez <xref:System.SerializableAttribute> öznitelik, numaralandırma uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-138">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="a8f5e-139">Olgu, <xref:System.Runtime.Serialization.DataContractSerializer> sınıf uyar <xref:System.NonSerializedAttribute> numaralandırma üyelerine uygulanan öznitelik davranışından farklıdır <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-139">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="a8f5e-140">Bu serileştiricileri her ikisi de Yoksay <xref:System.NonSerializedAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-140">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="a8f5e-141">Bayrak numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a8f5e-141">Flag Enumerations</span></span>  
 <span data-ttu-id="a8f5e-142">Uygulayabileceğiniz <xref:System.FlagsAttribute> özniteliği numaralandırmalar için.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-142">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="a8f5e-143">Bu durumda, sıfır veya daha fazla numaralandırma değerlerinin listesini gönderilebilecek veya aynı anda aldı.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-143">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="a8f5e-144">Bunu yapmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bayrak sabit ve iki tabanların tüm üyeleri işaretlemek <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-144">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="a8f5e-145">Bayrak sabit kullanmak için ilerlemeyi 2 (örneğin, 1, 2, 4, 8, 16, 32, 64) tabanların kesintisiz bir dizi olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-145">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="a8f5e-146">Bir bayrağın numaralandırma değeri göndermek için aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="a8f5e-146">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1.  <span data-ttu-id="a8f5e-147">Bir numaralandırma üyesine bulmaya (ile <xref:System.Runtime.Serialization.EnumMemberAttribute> uygulanan öznitelik) sayısal değer eşler.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-147">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="a8f5e-148">Varsa bulunan, yalnızca bu üyeyi içeren bir liste göndermek.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-148">If found, send a list that contains just that member.</span></span>  
  
2.  <span data-ttu-id="a8f5e-149">Vardır numaralandırma üyeleri, sayısal değer toplam kesme girişimi (her biri <xref:System.Runtime.Serialization.EnumMemberAttribute> uygulanan öznitelik) toplamı her bir parçasını eşleyin.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-149">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="a8f5e-150">Bu tüm üyelerin listesi gönderin.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-150">Send the list of all these members.</span></span> <span data-ttu-id="a8f5e-151">Unutmayın *doyumsuz algoritması* böyle bir toplam bulmak için kullanılır ve bu nedenle, mevcut olsa bile, bu tür bir toplam bulunan garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-151">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="a8f5e-152">Bu sorunu önlemek için numaralandırma üyeleri sayısal değerleri iki tabanların olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-152">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3.  <span data-ttu-id="a8f5e-153">Önceki iki adımı başarısız ve sayısal değerin sıfır ise, throw bir <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-153">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="a8f5e-154">Sayısal değer sıfır ise, boş bir liste gönderin.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-154">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8f5e-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8f5e-155">Example</span></span>  
 <span data-ttu-id="a8f5e-156">Aşağıdaki numaralandırma örnek bayrağı işlemde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-156">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="a8f5e-157">Aşağıdaki örnek değerler belirtildiği gibi serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-157">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f5e-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f5e-158">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="a8f5e-159">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a8f5e-159">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="a8f5e-160">Hizmet Anlaşmalarında Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="a8f5e-160">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
