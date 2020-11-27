---
title: Veri Sözleşmelerinde Numaralandırma Türleri
description: Veri anlaşması modelinin Numaralandırmaların, WFC programlama modelinin bir parçası olarak nasıl ifade olduğunu öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 88bf2513435a9c00cf11a0681b32871992c8d2b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276665"
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="d40f8-103">Veri Sözleşmelerinde Numaralandırma Türleri</span><span class="sxs-lookup"><span data-stu-id="d40f8-103">Enumeration Types in Data Contracts</span></span>

<span data-ttu-id="d40f8-104">Numaralandırmalar veri sözleşmesi modelinde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-104">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="d40f8-105">Bu konuda, programlama modelini açıklayan birkaç örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-105">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="d40f8-106">Sabit Listesi temelleri</span><span class="sxs-lookup"><span data-stu-id="d40f8-106">Enumeration Basics</span></span>  

 <span data-ttu-id="d40f8-107">Veri anlaşması modelinde numaralandırma türlerini kullanmanın bir yolu, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini türüne uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="d40f8-107">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="d40f8-108">Daha sonra, <xref:System.Runtime.Serialization.EnumMemberAttribute> veri sözleşmesine dahil olması gereken her üyeye özniteliğini uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-108">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="d40f8-109">Aşağıdaki örnekte iki sınıf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-109">The following example shows two classes.</span></span> <span data-ttu-id="d40f8-110">İlki numaralandırmayı kullanır ve ikincisi numaralandırmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d40f8-110">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="d40f8-111">Sınıfının bir örneği `Car` yalnızca `condition` alan, veya değerlerinden birine ayarlanmışsa gönderilebilir veya alınabilir `New` `Used` `Rental` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-111">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="d40f8-112">`condition`Veya ise, `Broken` `Stolen` bir oluşturulur <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-112">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="d40f8-113"><xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> Sıralama verileri sözleşmeleri için her zamanki gibi özellikleri (ve) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d40f8-113">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="d40f8-114">Sabit listesi üyesi değerleri</span><span class="sxs-lookup"><span data-stu-id="d40f8-114">Enumeration Member Values</span></span>  

 <span data-ttu-id="d40f8-115">Genellikle veri sözleşmesi sayısal değerleri değil sabit listesi üye adlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-115">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="d40f8-116">Ancak, veri anlaşması modelini kullanırken, alıcı tarafı bir WCF istemcesede, bu şema sayısal değerleri korur.</span><span class="sxs-lookup"><span data-stu-id="d40f8-116">However, when using the data contract model, if the receiving side is a WCF client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="d40f8-117">Bu, [XmlSerializer sınıfı kullanılarak](using-the-xmlserializer-class.md)kullanılırken bu durum değildir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-117">Note that this is not the case when using the [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="d40f8-118">Önceki örnekte, `condition` olarak ayarlanmışsa `Used` ve veriler XML olarak serileştirilildiğinde, sonuçta elde edilen XML `<condition>Used</condition>` değildir `<condition>1</condition>` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-118">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="d40f8-119">Bu nedenle, aşağıdaki veri sözleşmesi veri sözleşmesiyle eşdeğerdir `CarConditionEnum` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-119">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="d40f8-120">Örneğin, `CarConditionEnum` gönderme ve alma tarafında ' ı kullanabilirsiniz `CarConditionWithNumbers` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-120">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="d40f8-121">Gönderme tarafı için "1" değerini, ancak `Used` alan tarafı "20" değerini kullanıyorsa, XML temsili `<condition>Used</condition>` her iki taraf için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d40f8-121">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="d40f8-122">Veri sözleşmesine eklenmek için özniteliği uygulamanız gerekir <xref:System.Runtime.Serialization.EnumMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-122">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="d40f8-123">.NET Framework, her zaman bir numaralandırma için varsayılan değer olan 0 (sıfır) özel değerini bir numaralandırmaya uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d40f8-123">In the .NET Framework, you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="d40f8-124">Ancak, bu özel sıfır değeri, özniteliğiyle işaretlenmedikçe seri hale getirilemez <xref:System.Runtime.Serialization.EnumMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-124">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="d40f8-125">Bunun için iki özel durum vardır:</span><span class="sxs-lookup"><span data-stu-id="d40f8-125">There are two exceptions to this:</span></span>  
  
- <span data-ttu-id="d40f8-126">Bayrak numaralandırmalar (Bu konunun ilerleyen kısımlarında açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="d40f8-126">Flag enumerations (discussed later in this topic).</span></span>  
  
- <span data-ttu-id="d40f8-127">Özelliği olarak ayarlanmış sabit listesi veri üyeleri <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false` (Bu durumda, sıfır değerine sahip sabit listesi serileştirilmiş verilerden çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="d40f8-127">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="d40f8-128">Numaralandırma üyesi değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d40f8-128">Customizing Enumeration Member Values</span></span>  

 <span data-ttu-id="d40f8-129">Özniteliğin özelliğini kullanarak veri sözleşmesinin bir parçasını oluşturan sabit listesi üye değerini özelleştirebilirsiniz <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> <xref:System.Runtime.Serialization.EnumMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-129">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="d40f8-130">Örneğin, aşağıdaki veri sözleşmesi, veri sözleşmesine de eşdeğerdir `CarConditionEnum` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-130">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="d40f8-131">Serileştirilmiş olduğunda, değerinin `PreviouslyOwned` XML temsili vardır `<condition>Used</condition>` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-131">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="d40f8-132">Basit numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d40f8-132">Simple Enumerations</span></span>  

 <span data-ttu-id="d40f8-133">Ayrıca özniteliğin uygulanmadığı numaralandırma türlerini seri hale getirebilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-133">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="d40f8-134">Bu tür numaralandırma türleri, her üyenin ( <xref:System.NonSerializedAttribute> özniteliği uygulanmamış), öznitelik uygulanmış gibi değerlendirildiğinden, tam olarak açıklandığı gibi değerlendirilir <xref:System.Runtime.Serialization.EnumMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-134">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="d40f8-135">Örneğin, aşağıdaki numaralandırmada, önceki örneğe denk olarak bir veri anlaşması vardır `CarConditionEnum` .</span><span class="sxs-lookup"><span data-stu-id="d40f8-135">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="d40f8-136">Numaralandırmanın veri sözleşmesi adını ve ad alanını ve numaralandırma üyesi değerlerini özelleştirmeniz gerekmiyorsa basit numaralandırmalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d40f8-136">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="d40f8-137">Basit Numaralandırmalar hakkında notlar</span><span class="sxs-lookup"><span data-stu-id="d40f8-137">Notes on Simple Enumerations</span></span>  

 <span data-ttu-id="d40f8-138"><xref:System.Runtime.Serialization.EnumMemberAttribute>Özniteliği basit numaralandırmalara uygulamak hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-138">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="d40f8-139"><xref:System.SerializableAttribute>Özniteliğin numaralandırmaya uygulanıp uygulanmadığı fark etmez.</span><span class="sxs-lookup"><span data-stu-id="d40f8-139">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="d40f8-140"><xref:System.Runtime.Serialization.DataContractSerializer>Sınıfın, <xref:System.NonSerializedAttribute> numaralandırma üyelerine uygulanan özniteliği, ve ' nin davranışından farklı olduğunu unutmayın <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-140">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="d40f8-141">Bu serileştiricilerin her ikisi de <xref:System.NonSerializedAttribute> özniteliğini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="d40f8-141">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="d40f8-142">Bayrak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d40f8-142">Flag Enumerations</span></span>  

 <span data-ttu-id="d40f8-143"><xref:System.FlagsAttribute>Özniteliği numaralandırmalara uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d40f8-143">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="d40f8-144">Bu durumda, sıfır veya daha fazla numaralandırma değeri listesi aynı anda gönderilebilir veya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-144">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="d40f8-145">Bunu yapmak için, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bayrak numaralandırmasında uygulayın ve sonra iki üsse olan tüm üyeleri <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="d40f8-145">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="d40f8-146">Bayrak numaralandırması kullanmak için, ilerlemeyi 2 ' nin (örneğin, 1, 2, 4, 8, 16, 32, 64) kesintisiz bir dizi olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d40f8-146">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="d40f8-147">Bir bayrağın numaralandırma değerini göndermek için aşağıdaki adımlar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d40f8-147">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1. <span data-ttu-id="d40f8-148">Sayısal değerle eşlenen bir numaralandırma üyesi ( <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulanmış olan) bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d40f8-148">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="d40f8-149">Bulunursa, yalnızca o üyeyi içeren bir liste gönderin.</span><span class="sxs-lookup"><span data-stu-id="d40f8-149">If found, send a list that contains just that member.</span></span>  
  
2. <span data-ttu-id="d40f8-150">Toplamın her bir bölümüyle eşlenen numaralandırma üyeleri (her biri uygulanmış olan özniteliği) gibi bir toplama göre sayısal değeri kesmeyi deneyin <xref:System.Runtime.Serialization.EnumMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-150">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="d40f8-151">Tüm bu üyelerin listesini gönderin.</span><span class="sxs-lookup"><span data-stu-id="d40f8-151">Send the list of all these members.</span></span> <span data-ttu-id="d40f8-152">Bu tür bir toplamı bulmak için *doyumsuz algoritmasının* kullanıldığını ve bu nedenle söz konusu toplamın mevcut olsa bile nerede bulunduğunu garanti etmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d40f8-152">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="d40f8-153">Bu sorundan kaçınmak için, numaralandırma üyelerinin sayısal değerlerinin ikiye üsleri olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d40f8-153">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3. <span data-ttu-id="d40f8-154">Yukarıdaki iki adım başarısız olursa ve sayısal değer sıfır değilse, oluşturun <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="d40f8-154">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="d40f8-155">Sayısal değer sıfırsa boş listeyi gönderin.</span><span class="sxs-lookup"><span data-stu-id="d40f8-155">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d40f8-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="d40f8-156">Example</span></span>  

 <span data-ttu-id="d40f8-157">Aşağıdaki numaralandırma örneği bir bayrak işleminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-157">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="d40f8-158">Aşağıdaki örnek değerler belirtilen şekilde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="d40f8-158">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d40f8-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d40f8-159">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="d40f8-160">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d40f8-160">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="d40f8-161">Hizmet Sözleşmelerinde Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="d40f8-161">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)
