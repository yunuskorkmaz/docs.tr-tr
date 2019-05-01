---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 8d2825ff738ffc50ba9a438024db27aff5686a0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870350"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama
Aşağıdaki kod örneği için uyar bir bileşeni kullanmak gösterilmiştir [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Bu örnekte bir form kullanır `PrimeNumberCalculator` açıklanan bileşen [nasıl yapılır: Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Bu örnekte bir projeyi çalıştırdığınızda, bir kılavuz "Asal sayı hesaplayıcı" form ve iki düğme görürsünüz: **Yeni görev Başlat** ve **iptal**. Tıklayabilirsiniz **yeni görev Başlat** düğmesine birkaç kez art arda ve her bir click için rastgele oluşturulmuş test birkaç asal olup olmadığını belirlemek için bir hesaplama zaman uyumsuz bir işlem başlar. Form düzenli ilerleme ve artımlı sonuçlarını görüntüler. Her işlemin benzersiz bir görev kimliği atanır Hesaplama sonucu görüntülenen **sonucu** sütun; test sayı prime değilse olarak etiketlenir **bileşik,** ve kendi ilk bölen görüntülenir.  
  
 Bekleyen işlemi ile iptal edilebilir **iptal** düğmesi. Birden çok seçim yapılabilir.  
  
> [!NOTE]
>  Çoğu sayı üssü olmayacaktır. Birden fazla tamamlanmış işlemlerinden sonra asal bulunan değil, yalnızca daha fazla görev başlatın ve bazı asal sayıları sonunda bulabilirsiniz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
