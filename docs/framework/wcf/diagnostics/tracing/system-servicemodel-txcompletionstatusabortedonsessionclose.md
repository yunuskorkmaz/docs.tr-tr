---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: f41fd08138591a90b6173b5e4806e5ac73ff07da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662770"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="61be2-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="61be2-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="61be2-103">Bu oturumu kapatıldı ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute false olarak ayarlanmış tamamlanmamış olduğundan belirtilen işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="61be2-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="61be2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61be2-104">Description</span></span>  
 <span data-ttu-id="61be2-105">Geçerli etkin oturum kapatıldığında, işlem tamamlanmadı ve TransactionAutoCompleteOnSessionClose ayarlandığında izlenen `false`.</span><span class="sxs-lookup"><span data-stu-id="61be2-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="61be2-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="61be2-106">Troubleshooting</span></span>  
 <span data-ttu-id="61be2-107">Bu izleme araştırılması gereken olası bir uygulama hatası gösterir.</span><span class="sxs-lookup"><span data-stu-id="61be2-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61be2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61be2-108">See also</span></span>
- [<span data-ttu-id="61be2-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="61be2-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="61be2-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="61be2-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="61be2-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="61be2-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
