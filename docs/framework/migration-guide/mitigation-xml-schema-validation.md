---
title: 'Azaltma: XML Şema Doğrulaması'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 7feed7de4a6c76f5f2ba0e2ea1c532aad6bde4de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126066"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="f349a-102">Azaltma: XML Şema Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f349a-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="f349a-103">.NET Framework 4,6 ' de, bir bileşik anahtar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması benzersiz kısıtlamanın ihlal edildiğini algılar.</span><span class="sxs-lookup"><span data-stu-id="f349a-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f349a-104">Etki</span><span class="sxs-lookup"><span data-stu-id="f349a-104">Impact</span></span>  
 <span data-ttu-id="f349a-105">Bu değişikliğin etkisi en az olmalıdır: şema belirtimine göre, `xsd:unique` boş bir anahtarla bileşik anahtar kullanılarak ihlal edilirse bir şema doğrulama hatası beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f349a-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f349a-106">Azaltma</span><span class="sxs-lookup"><span data-stu-id="f349a-106">Mitigation</span></span>  
 <span data-ttu-id="f349a-107">Bir bileşik anahtarda bir boş anahtar varsa bir şema doğrulama hatası algılanıp algılanmayacağı, yapılandırılabilir bir özelliktir:</span><span class="sxs-lookup"><span data-stu-id="f349a-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="f349a-108">.NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, şema doğrulama hatası algılama işlemi varsayılan olarak etkindir; Ancak, şema doğrulama hatası algılanmayacak şekilde devre dışı bırakmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f349a-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="f349a-109">.NET Framework 4,6 altında çalışan ancak .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, varsayılan olarak bir şema doğrulama hatası algılanmadı; Ancak, şema doğrulama hatasının algılanabilmesi için onu kabul etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f349a-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="f349a-110">Bu davranış, `System.Xml.IgnoreEmptyKeySequences` anahtarın değerini tanımlamak için <xref:System.AppContext> sınıfı kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f349a-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="f349a-111">Anahtarın varsayılan değeri `false` (boş anahtar dizileri yok sayılıyor), .NET Framework 4,6 ' i hedefleyen uygulamalar, anahtarın değerini `true`olarak ayarlamak için aşağıdaki kodu kullanarak davranışı geri alabilir:</span><span class="sxs-lookup"><span data-stu-id="f349a-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="f349a-112">.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalar için, anahtarın varsayılan değeri `true` (boş anahtar dizileri yoksayıldı), boş anahtara sahip bir bileşik anahtarın, bir şema doğrulama hatası oluşturduğundan Aşağıdaki kod, anahtarın değerini `false`olarak ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="f349a-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f349a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f349a-113">See also</span></span>

- [<span data-ttu-id="f349a-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f349a-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
