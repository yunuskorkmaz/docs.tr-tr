---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 0d8c77d01351b0c62e0186e5aee69ca70aebe15e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274328"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="1886f-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="1886f-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>

<span data-ttu-id="1886f-103">Oturum kapatıldığında tamamlanmamış olduğundan ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute yanlış olarak ayarlandığı için belirtilen işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1886f-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1886f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1886f-104">Description</span></span>  

 <span data-ttu-id="1886f-105">Geçerli etkin oturum kapalıysa izlenen, işlem tamamlanmadıysa ve TransactionAutoCompleteOnSessionClose olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="1886f-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1886f-106">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1886f-106">Troubleshooting</span></span>  

 <span data-ttu-id="1886f-107">Bu izleme, araştırılması gereken olası bir uygulama hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1886f-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1886f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1886f-108">See also</span></span>

- [<span data-ttu-id="1886f-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="1886f-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="1886f-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1886f-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1886f-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="1886f-111">Administration and Diagnostics</span></span>](../index.md)
