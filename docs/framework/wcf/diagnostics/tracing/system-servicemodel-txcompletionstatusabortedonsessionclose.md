---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 149a2bfac435185552c3871948b35bc860a43ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="5d9be-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="5d9be-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="5d9be-103">Bu oturum kapatıldı ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute false olarak ayarladığınızda, tamamlanmamış olduğundan belirtilen işlem durduruldu.</span><span class="sxs-lookup"><span data-stu-id="5d9be-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5d9be-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d9be-104">Description</span></span>  
 <span data-ttu-id="5d9be-105">Geçerli etkin oturum kapatıldı, işlem tamamlanmadı ve TransactionAutoCompleteOnSessionClose ayarlanmış izlenen `false`.</span><span class="sxs-lookup"><span data-stu-id="5d9be-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5d9be-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="5d9be-106">Troubleshooting</span></span>  
 <span data-ttu-id="5d9be-107">Bu izleme araştırılması gereken olası bir uygulama hatası gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d9be-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9be-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d9be-108">See Also</span></span>  
 [<span data-ttu-id="5d9be-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="5d9be-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5d9be-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="5d9be-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5d9be-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="5d9be-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
