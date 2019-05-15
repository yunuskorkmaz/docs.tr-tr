---
title: 'Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: 14326d793be3ee71022a7a1e7398b9af469aab10
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592452"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme
Denetimlere bağlayabilirsiniz önerilmesine özel durumlar ve hatalar temel alınan iş nesnelerde ortaya çıkar. Bu hatalar ve özel durumlar ıntercept ve sonra kurtarmak veya hata bilgilerini kullanıcıya işleyerek geçirmek <xref:System.Windows.Forms.Binding.BindingComplete> belirli bir olay <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, veya <xref:System.Windows.Forms.CurrencyManager> bileşeni.  
  
## <a name="example"></a>Örnek  
 Bu kod örneği, hataları ve veri bağlama işlemi sırasında oluşan özel durumlarının nasıl ele alınacağını göstermektedir. Hataları işleyerek ıntercept yapmayı gösteren <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> olayı <xref:System.Windows.Forms.Binding> nesneleri. Hataları ve özel durumları bu olayı işleme tarafından müdahale için bağını biçimlendirme etkinleştirmeniz gerekir. Bağlama oluşturulmuş ya da eklenen bağlama koleksiyonuna veya ayarlayarak biçimlendirme etkinleştirebilirsiniz <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> özelliğini `true`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 Ne zaman kodu çalıştıran ve boş bir dize bölümü ad veya değer 100'den daha az girilen parça numarası için bir ileti kutusu görünür girilir. Bu bir işleme sonucudur <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> bu metin bağlamaları için olay.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [BindingSource Bileşeni](bindingsource-component.md)
