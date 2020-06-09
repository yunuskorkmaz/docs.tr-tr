---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: c398fc52d5924c033500b95924f9287b43cc9e9d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576609"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="14163-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="14163-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="14163-103">Oturum kapatıldığında tamamlanmamış olduğundan ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute yanlış olarak ayarlandığı için belirtilen işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="14163-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="14163-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14163-104">Description</span></span>  
 <span data-ttu-id="14163-105">Geçerli etkin oturum kapalıysa izlenen, işlem tamamlanmadıysa ve TransactionAutoCompleteOnSessionClose olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="14163-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="14163-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="14163-106">Troubleshooting</span></span>  
 <span data-ttu-id="14163-107">Bu izleme, araştırılması gereken olası bir uygulama hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14163-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14163-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14163-108">See also</span></span>

- [<span data-ttu-id="14163-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="14163-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="14163-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="14163-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="14163-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="14163-111">Administration and Diagnostics</span></span>](../index.md)
