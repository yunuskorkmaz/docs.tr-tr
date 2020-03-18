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
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "69950714"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama
Aşağıdaki kod örneği, [Olay tabanlı Asynchronous Desen Genel Bakış'a](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)uyan bir bileşenin nasıl kullanılacağını gösterir. Bu örnekteki form, `PrimeNumberCalculator` Nasıl [Tanımlanır: Olay tabanlı Asynchronous Deseni destekleyen bir Bileşeni Uygulama'da](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)açıklanan bileşeni kullanır.  
  
 Bu örneği kullanan bir proje çalıştırdığınızda, ızgaralı ve iki düğmeli bir "Asal Sayı Hesapmakinesi" formu görürsünüz: **Yeni Görevi Başlat** ve İptal **Et.** Yeni Görev **Başlat** düğmesini art arda birkaç kez tıklatabilirsiniz ve her tıklama için, rasgele oluşturulan test numarasının asal olup olmadığını belirlemek için bir hesaplama başlatılır. Form periyodik olarak ilerleme ve artımlı sonuçları görüntüler. Her işlem benzersiz bir görev kimliği atanır. Hesaplama sonucu **Sonuç** sütununda görüntülenir; test numarası asal değilse, **Bileşik** olarak etiketlenir ve ilk bölengörüntülenir.  
  
 Bekleyen herhangi bir işlem **İptal** düğmesi ile iptal edilebilir. Birden çok seçim yapılabilir.  
  
> [!NOTE]
> Çoğu sayı asal olmaz. Tamamlanan birkaç işlemden sonra bir asal sayı bulamadıysanız, daha fazla görev başlatmanız yeterlidir ve sonunda bazı asal sayılar bulacaksınız.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
