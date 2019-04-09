---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166510"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="a3d70-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="a3d70-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="a3d70-103">Bu oturumu kapatıldı ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute false olarak ayarlanmış tamamlanmamış olduğundan belirtilen işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="a3d70-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a3d70-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d70-104">Description</span></span>  
 <span data-ttu-id="a3d70-105">Geçerli etkin oturum kapatıldığında, işlem tamamlanmadı ve TransactionAutoCompleteOnSessionClose ayarlandığında izlenen `false`.</span><span class="sxs-lookup"><span data-stu-id="a3d70-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a3d70-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="a3d70-106">Troubleshooting</span></span>  
 <span data-ttu-id="a3d70-107">Bu izleme araştırılması gereken olası bir uygulama hatası gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3d70-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d70-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3d70-108">See also</span></span>

- [<span data-ttu-id="a3d70-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="a3d70-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a3d70-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="a3d70-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a3d70-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="a3d70-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
