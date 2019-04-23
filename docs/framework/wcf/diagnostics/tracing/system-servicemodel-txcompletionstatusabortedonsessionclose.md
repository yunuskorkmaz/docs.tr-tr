---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166510"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="86c46-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="86c46-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="86c46-103">Bu oturumu kapatıldı ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute false olarak ayarlanmış tamamlanmamış olduğundan belirtilen işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="86c46-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="86c46-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86c46-104">Description</span></span>  
 <span data-ttu-id="86c46-105">Geçerli etkin oturum kapatıldığında, işlem tamamlanmadı ve TransactionAutoCompleteOnSessionClose ayarlandığında izlenen `false`.</span><span class="sxs-lookup"><span data-stu-id="86c46-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="86c46-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="86c46-106">Troubleshooting</span></span>  
 <span data-ttu-id="86c46-107">Bu izleme araştırılması gereken olası bir uygulama hatası gösterir.</span><span class="sxs-lookup"><span data-stu-id="86c46-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c46-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c46-108">See also</span></span>

- [<span data-ttu-id="86c46-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="86c46-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="86c46-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="86c46-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="86c46-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="86c46-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
