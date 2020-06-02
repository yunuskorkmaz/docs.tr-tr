---
title: Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: f10b4ae5617edc8cf8a38a6cbac999e10a935dc2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291389"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
Zaman uyumsuz bir işlemin sonuçlarını beklerken diğer işleri yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellemez. Zaman uyumsuz bir işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için şu seçeneklerden birini kullanın:  
  
- <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> İşlemin tamamlanıp tamamlanmadığını anlamak için, zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın. Bu yaklaşım yoklama olarak bilinir ve bu konuda gösterilmiştir.  
  
- <xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullanın. Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bir bilgisayar Için etki alanı adı sistem bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir. Bu örnek, zaman uyumsuz işlemi başlatır ve sonra işlem tamamlanana kadar konsola (".") nokta (".") yazdırır. **null** **Nothing** <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> <xref:System.Object> Bu yaklaşım kullanılırken bu bağımsız değişkenler gerekli olmadığından, ve parametreleri için null (Visual Basic hiçbir şey yok) geçtiğini unutmayın.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
