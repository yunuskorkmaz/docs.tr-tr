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
ms.openlocfilehash: 08cd9e0a167d1bef9bbe6437b22985082c80e5f9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365808"
---
# <a name="handwriting-recognition"></a>El Yazısı Tanıma
Dijital Mürekkep WPF platformu ile ilgili olarak bu bölümde tanıma temelleri ele alınmaktadır.  
  
## <a name="recognition-solutions"></a>Tanıma çözümleri  
 Aşağıdaki örnek mürekkep kullanarak anlamayı gösterir [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) sınıfı.  
  
> [!NOTE]
>  Bu örnek, yükseltirseniz sistemde yüklü olmasını gerektirir.  
  
 Visual Studio adlı yeni bir WPF uygulaması projesi oluşturma **InkRecognition**. Gt;Window1.xaml dosyasının içeriğini aşağıdaki XAML kod ile değiştirin. Bu kod, uygulamanın kullanıcı arabirimini işler.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 \Program Files\Microsoft Shared\Ink içinde bulunan Microsoft.Ink.dll Microsoft Ink derlemesine bir başvuru ekleyin. Arka plan kod dosyasında içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
