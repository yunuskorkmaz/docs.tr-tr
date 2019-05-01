---
title: 'Nasıl yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2d61ba254a76235a12ca5dda23fdecb8838ae75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015024"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Nasıl yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme
Aşağıdaki örnek, olacak bir temsilci kaydettirmek gösterilmektedir ne zaman çağrılır bir <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özellik için bir çağrı nedeniyle true olur <xref:System.Threading.CancellationTokenSource.Cancel%2A> belirteç oluşturulan nesne. Zaman uyumsuz bir işlemin tamamlanmasını bekleyen engellemeyi kaldırma yöntemleri yanı sıra, birleşik iptalini çerçevesi yerel olarak desteklemeyen zaman uyumsuz işlemleri iptal etmek için bu tekniği kullanın.  
  
> [!NOTE]
>  "Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci İptal istendiğinde çağrılacak yöntem olarak kaydedilir.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Geri çağırma kaydedildiğinde, zaten iptal istendi, geri çağırma çağrılacak yine de garanti edilir. Bu özel durumda <xref:System.Net.WebClient.CancelAsync%2A> yöntemi yaparsanız hiçbir şey her zaman güvenli bir yöntem çağırmak, bu nedenle hiçbir zaman uyumsuz bir işlem devam ediyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
