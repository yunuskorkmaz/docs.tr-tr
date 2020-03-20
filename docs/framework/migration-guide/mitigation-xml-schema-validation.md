---
title: 'Azaltma: XML Şema Doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457743"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="15a5c-102">Azaltma: XML Şema Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="15a5c-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="15a5c-103">.NET Framework 4.6'da, bileşik anahtar kullanılıyorsa ve bir anahtar boşsa XSD şema doğrulaması benzersiz kısıtlamanın ihlalini algılar.</span><span class="sxs-lookup"><span data-stu-id="15a5c-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="15a5c-104">Etki</span><span class="sxs-lookup"><span data-stu-id="15a5c-104">Impact</span></span>  
 <span data-ttu-id="15a5c-105">Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, boş anahtarlı `xsd:unique` bileşik anahtar kullanılarak ihlal edilirse şema doğrulama hatası beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="15a5c-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="15a5c-106">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="15a5c-106">Mitigation</span></span>  
 <span data-ttu-id="15a5c-107">Bileşik bir anahtarda boş bir anahtar varsa şema doğrulama hatasının algılanıp algılanmadığı yapılandırılabilir bir özelliktir:</span><span class="sxs-lookup"><span data-stu-id="15a5c-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="15a5c-108">.NET Framework 4.6'yı hedefleyen uygulamalardan başlayarak, şema doğrulama hatasının algılanması varsayılan olarak etkinleştirilir; ancak, şema doğrulama hatası algılanmaması için bu hatayı devre dışı bırakmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="15a5c-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="15a5c-109">.NET Framework 4.6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalarda varsayılan olarak bir şema doğrulama hatası algılanmaz; ancak, şema doğrulama hatası algılanacak şekilde, bunu tercih etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="15a5c-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="15a5c-110">Bu <xref:System.AppContext> `System.Xml.IgnoreEmptyKeySequences` davranış, anahtarın değerini tanımlamak için sınıf kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="15a5c-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="15a5c-111">Anahtarın varsayılan değeri (boş anahtar dizileri göz ardı edilmez) olduğundan, `false` .NET Framework 4.6'yı hedefleyen uygulamalar anahtarın değerini ayarlamak `true`için aşağıdaki kodu kullanarak davranışı devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15a5c-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="15a5c-112">.NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalariçin, anahtarın `true` varsayılan değeri (boş anahtar dizileri yoksayılır) olduğundan, boş anahtara sahip bileşik anahtarın anahtarın değerini ayarlamak için aşağıdaki `false`kodu kullanarak şema doğrulama hatası oluşturduğundan emin olmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="15a5c-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="15a5c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15a5c-113">See also</span></span>

- [<span data-ttu-id="15a5c-114">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="15a5c-114">Application compatibility</span></span>](application-compatibility.md)
