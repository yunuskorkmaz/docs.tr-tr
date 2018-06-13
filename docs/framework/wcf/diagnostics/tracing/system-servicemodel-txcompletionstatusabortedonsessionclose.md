---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7ecc70f1c4d7184401dd29908968f628f2e6792a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484220"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="35569-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="35569-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="35569-103">Bu oturum kapatıldı ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute false olarak ayarladığınızda, tamamlanmamış olduğundan belirtilen işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="35569-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="35569-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35569-104">Description</span></span>  
 <span data-ttu-id="35569-105">Geçerli etkin oturum kapatıldı, işlem tamamlanmadı ve TransactionAutoCompleteOnSessionClose ayarlanmış izlenen `false`.</span><span class="sxs-lookup"><span data-stu-id="35569-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="35569-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="35569-106">Troubleshooting</span></span>  
 <span data-ttu-id="35569-107">Bu izleme araştırılması gereken olası bir uygulama hatası gösterir.</span><span class="sxs-lookup"><span data-stu-id="35569-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35569-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35569-108">See Also</span></span>  
 [<span data-ttu-id="35569-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="35569-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="35569-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="35569-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="35569-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="35569-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
