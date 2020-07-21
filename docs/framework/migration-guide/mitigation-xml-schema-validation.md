---
title: 'Azaltma: XML Şema Doğrulaması'
description: Bir bileşik anahtar kullanılmışsa ve .NET Framework 4,6 ' de bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 0672361ca5c0bc7cb6ec166f59278b93555e0947
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475313"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="0753f-103">Azaltma: XML Şema Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0753f-103">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="0753f-104">.NET Framework 4,6 ' de, bir bileşik anahtar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.</span><span class="sxs-lookup"><span data-stu-id="0753f-104">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0753f-105">Etki</span><span class="sxs-lookup"><span data-stu-id="0753f-105">Impact</span></span>  
 <span data-ttu-id="0753f-106">Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, `xsd:unique` boş bir anahtarla bir bileşik anahtar kullanılarak ihlal edilirse bir şema doğrulama hatası beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0753f-106">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0753f-107">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="0753f-107">Mitigation</span></span>  
 <span data-ttu-id="0753f-108">Bir bileşik anahtarda bir boş anahtar varsa bir şema doğrulama hatası algılanıp algılanmayacağı, yapılandırılabilir bir özelliktir:</span><span class="sxs-lookup"><span data-stu-id="0753f-108">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="0753f-109">.NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, şema doğrulama hatası algılama işlemi varsayılan olarak etkindir; Ancak, şema doğrulama hatası algılanmayacak şekilde devre dışı bırakmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0753f-109">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="0753f-110">.NET Framework 4,6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatasının algılanabilmesi için onu kabul etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0753f-110">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="0753f-111">Bu davranış, <xref:System.AppContext> anahtarın değerini tanımlamak için sınıfı kullanılarak yapılandırılabilir `System.Xml.IgnoreEmptyKeySequences` .</span><span class="sxs-lookup"><span data-stu-id="0753f-111">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="0753f-112">Anahtarın varsayılan değeri `false` (boş anahtar dizileri yoksayılamadığından) olduğundan, .NET Framework 4,6 ' i hedefleyen uygulamalar, anahtarın değerini olarak ayarlamak için aşağıdaki kodu kullanarak davranışı geri alabilir `true` :</span><span class="sxs-lookup"><span data-stu-id="0753f-112">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="0753f-113">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalar için, anahtarın varsayılan değeri `true` (boş anahtar dizileri yoksayıldı) olduğundan, boş anahtara sahip bir bileşik anahtarın, anahtarın değerini olarak ayarlamak için aşağıdaki kodu kullanarak bir şema doğrulama hatası oluşturduğundan emin olabilirsiniz `false` .</span><span class="sxs-lookup"><span data-stu-id="0753f-113">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0753f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0753f-114">See also</span></span>

- [<span data-ttu-id="0753f-115">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="0753f-115">Application compatibility</span></span>](application-compatibility.md)
