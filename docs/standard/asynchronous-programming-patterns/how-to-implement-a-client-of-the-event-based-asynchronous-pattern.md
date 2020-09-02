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
ms.openlocfilehash: d0253745d4d2ee90f355364ed1b1b0d9b74d0fc1
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379193"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama
Aşağıdaki kod örneği, [olay tabanlı zaman uyumsuz düzene genel bakış](event-based-asynchronous-pattern-overview.md)'a uygun bir bileşenin nasıl kullanılacağını göstermektedir. Bu örnek için form, `PrimeNumberCalculator` [nasıl yapılır: olay tabanlı zaman uyumsuz kalıbı destekleyen bir bileşeni uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)bölümünde açıklanan bileşeni kullanır.  
  
 Bu örneği kullanan bir projeyi çalıştırdığınızda, kılavuz ve iki düğme içeren bir "ana sayı Hesaplayıcı" formu görürsünüz: **Yeni görev başlatın** ve **iptal edin**. **Yeni görev Başlat** düğmesine art arda birkaç kez tıklayabilirsiniz ve her tıklama için zaman uyumsuz bir işlem, rastgele oluşturulmuş bir test numarasının asal olup olmadığını belirlemekte bir hesaplama başlatır. Form düzenli olarak ilerleme ve artımlı sonuçları görüntüleyecektir. Her işleme benzersiz bir görev KIMLIĞI atanır. Hesaplama sonucu **sonuç** sütununda görüntülenir; sınama numarası ana değilse, bileşik olarak etiketlenir ve ilk **böleni** görüntülenir.  
  
 Bekleyen tüm işlemler **iptal** düğmesi ile iptal edilebilir. Birden çok seçim yapılabilir.  
  
> [!NOTE]
> Çoğu sayı ana olmaz. Birkaç tamamlanmış işlemden sonra bir asal sayı bulmadıysanız, daha fazla görev başlatmanız yeterlidir ve sonuç olarak bazı asal sayılar bulacaksınız.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
