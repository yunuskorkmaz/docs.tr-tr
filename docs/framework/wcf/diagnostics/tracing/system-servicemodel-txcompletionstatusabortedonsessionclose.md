---
description: ': System. ServiceModel. TxCompletionStatusAbortedOnSessionClose hakkında daha fazla bilgi edinin'
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: d47dc1a87c7f44b58f70f9590b4233f1e0a9074e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735718"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="eb445-103">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="eb445-103">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>

<span data-ttu-id="eb445-104">Oturum kapatıldığında tamamlanmamış olduğundan ve TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute yanlış olarak ayarlandığı için belirtilen işlem iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="eb445-104">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="eb445-105">Description</span><span class="sxs-lookup"><span data-stu-id="eb445-105">Description</span></span>  

 <span data-ttu-id="eb445-106">Geçerli etkin oturum kapalıysa izlenen, işlem tamamlanmadıysa ve TransactionAutoCompleteOnSessionClose olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="eb445-106">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="eb445-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="eb445-107">Troubleshooting</span></span>  

 <span data-ttu-id="eb445-108">Bu izleme, araştırılması gereken olası bir uygulama hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb445-108">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb445-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb445-109">See also</span></span>

- [<span data-ttu-id="eb445-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="eb445-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="eb445-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb445-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="eb445-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="eb445-112">Administration and Diagnostics</span></span>](../index.md)
