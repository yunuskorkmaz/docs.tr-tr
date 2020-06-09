---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 0c53c1617f3aa3c5f16ba16e8ec548e46ce22137
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594341"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="b4869-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="b4869-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="b4869-103">Bir hazırlık iletisi yeniden denemesi, yanıt vermeyen bir katılımcıya gönderildi.</span><span class="sxs-lookup"><span data-stu-id="b4869-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b4869-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4869-104">Description</span></span>  
 <span data-ttu-id="b4869-105">Yerel Işlem yöneticisinin belirli bir sürede yanıt almadığı için bir uygulamayı bir alt katılımcıya yeniden göndermesi gerekiyorsa izleniyor.</span><span class="sxs-lookup"><span data-stu-id="b4869-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b4869-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="b4869-106">Troubleshooting</span></span>  
 <span data-ttu-id="b4869-107">Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.</span><span class="sxs-lookup"><span data-stu-id="b4869-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="b4869-108">Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="b4869-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="b4869-109">Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="b4869-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4869-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4869-110">See also</span></span>

- [<span data-ttu-id="b4869-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="b4869-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="b4869-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="b4869-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b4869-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="b4869-113">Administration and Diagnostics</span></span>](../index.md)
