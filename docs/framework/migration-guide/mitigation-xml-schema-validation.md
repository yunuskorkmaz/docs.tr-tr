---
title: 'Azaltma: XML Şema Doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457743"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="9afb6-102">Azaltma: XML Şema Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="9afb6-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="9afb6-103">.NET Framework 4,6 ' de, bir bileşik anahtar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.</span><span class="sxs-lookup"><span data-stu-id="9afb6-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9afb6-104">Etki</span><span class="sxs-lookup"><span data-stu-id="9afb6-104">Impact</span></span>  
 <span data-ttu-id="9afb6-105">Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, `xsd:unique` boş bir anahtarla bileşik anahtar kullanılarak ihlal edilirse bir şema doğrulama hatası beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="9afb6-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9afb6-106">Azaltma</span><span class="sxs-lookup"><span data-stu-id="9afb6-106">Mitigation</span></span>  
 <span data-ttu-id="9afb6-107">Bir bileşik anahtarda bir boş anahtar varsa bir şema doğrulama hatası algılanıp algılanmayacağı, yapılandırılabilir bir özelliktir:</span><span class="sxs-lookup"><span data-stu-id="9afb6-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="9afb6-108">.NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, şema doğrulama hatası algılama işlemi varsayılan olarak etkindir; Ancak, şema doğrulama hatası algılanmayacak şekilde devre dışı bırakmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9afb6-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="9afb6-109">.NET Framework 4,6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatasının algılanabilmesi için onu kabul etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9afb6-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="9afb6-110">Bu davranış, `System.Xml.IgnoreEmptyKeySequences` anahtarın değerini tanımlamak için <xref:System.AppContext> sınıfı kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9afb6-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="9afb6-111">Anahtarın varsayılan değeri `false` (boş anahtar dizileri yok sayılıyor), .NET Framework 4,6 ' i hedefleyen uygulamalar, anahtarın değerini `true`olarak ayarlamak için aşağıdaki kodu kullanarak davranışı geri alabilir:</span><span class="sxs-lookup"><span data-stu-id="9afb6-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="9afb6-112">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalar için, anahtarın varsayılan değeri `true` (boş anahtar dizileri yoksayıldı), boş anahtara sahip bir bileşik anahtarın, bir şema doğrulama hatası oluşturduğundan Aşağıdaki kod, anahtarın değerini `false`olarak ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="9afb6-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9afb6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9afb6-113">See also</span></span>

- [<span data-ttu-id="9afb6-114">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="9afb6-114">Application compatibility</span></span>](application-compatibility.md)
