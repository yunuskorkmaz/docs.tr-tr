---
title: "Azaltma: XML Şema Doğrulaması"
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
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd5e83da32e32b60f5d1584c7057e36a3851b8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="7e204-102">Azaltma: XML Şema Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7e204-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="7e204-103">İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD şema doğrulaması, bileşik bir anahtar kullanılıyor ve bir anahtar boş ise benzersiz kısıtlamayı ihlal algılar.</span><span class="sxs-lookup"><span data-stu-id="7e204-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="7e204-104">Etki</span><span class="sxs-lookup"><span data-stu-id="7e204-104">Impact</span></span>  
 <span data-ttu-id="7e204-105">Bu değişikliğin etkisini en az olmalıdır: şema belirtimine dayalı olarak, şema doğrulama hatası varsa beklenen `xsd:unique` boş bir anahtar ile bir bileşik anahtarı kullanılarak ihlal etti.</span><span class="sxs-lookup"><span data-stu-id="7e204-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="7e204-106">Azaltma</span><span class="sxs-lookup"><span data-stu-id="7e204-106">Mitigation</span></span>  
 <span data-ttu-id="7e204-107">Bileşik anahtar bir boş anahtar varsa, şema doğrulama hatası olup olmadığını algıladı yapılandırılabilir bir özelliğidir:</span><span class="sxs-lookup"><span data-stu-id="7e204-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="7e204-108">Hedefleyen uygulamalarla başlangıç [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], şema doğrulama hatası algılama, varsayılan olarak etkindir; böylece şema doğrulama hatası algılanmadı ancak bunun dışında geri çevirme mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7e204-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="7e204-109">Altında çalışacağı uygulamalarda [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ancak hedef [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] ve önceki sürümleri, varsayılan olarak bir şema doğrulama hatası algılanmadı; böylece şema doğrulama hatası algılandı ancak onu kabul etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7e204-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="7e204-110">Bu davranış kullanarak yapılandırılabilir <xref:System.AppContext> değerini tanımlamak için sınıf `System.Xml.IgnoreEmptyKeySequences` geçin.</span><span class="sxs-lookup"><span data-stu-id="7e204-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="7e204-111">Anahtarın varsayılan değeri olduğundan `false` (boş anahtar sıraları değil yoksayılır), hedef uygulamaları [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] dışında davranış anahtarın değerini ayarlamak için aşağıdaki kodu kullanarak seçebilirsiniz `true`:</span><span class="sxs-lookup"><span data-stu-id="7e204-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="7e204-112">Hedef uygulamalar için [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] ve önceki sürümleri, anahtarın varsayılan değeri olduğundan `true` (boş anahtar sıraları yoksayılır) kullanarak bir şema doğrulama hatası boş anahtarlı bileşik bir anahtar oluşturmak emin olmak mümkündür anahtarın değerini ayarlamak için kod aşağıdaki `false`.</span><span class="sxs-lookup"><span data-stu-id="7e204-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7e204-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e204-113">See Also</span></span>  
 [<span data-ttu-id="7e204-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7e204-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
