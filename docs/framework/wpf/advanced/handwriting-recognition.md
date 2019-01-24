---
title: El Yazısı Tanıma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: 8f520b80970bfeebdfea01a6c722634efd99ffe7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725395"
---
# <a name="handwriting-recognition"></a>El Yazısı Tanıma
Dijital Mürekkep WPF platformu ile ilgili olarak bu bölümde tanıma temelleri ele alınmaktadır.  
  
## <a name="recognition-solutions"></a>Tanıma çözümleri  
 Aşağıdaki örnek mürekkep kullanarak anlamayı gösterir [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) sınıfı.  
  
> [!NOTE]
>  Bu örnek, yükseltirseniz sistemde yüklü olmasını gerektirir.  
  
 Visual Studio adlı yeni bir WPF uygulaması projesi oluşturma **InkRecognition**. Gt;Window1.xaml dosyasının içeriğini aşağıdaki XAML kod ile değiştirin. Bu kod, uygulamanın kullanıcı arabirimini işler.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 \Program Files\Microsoft Shared\Ink içinde bulunan Microsoft.Ink.dll Microsoft Ink derlemesine bir başvuru ekleyin. Arka plan kod dosyasında içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
