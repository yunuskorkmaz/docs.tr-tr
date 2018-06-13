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
ms.openlocfilehash: d72d8b42a23205d8599b23a467677dd2f05d5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542382"
---
# <a name="handwriting-recognition"></a>El Yazısı Tanıma
WPF Platform dijital mürekkep ilgili olarak bu bölümde tanıma temelleri açıklanır.  
  
## <a name="recognition-solutions"></a>Tanıma çözümleri  
 Aşağıdaki örnek, mürekkep kullanarak tanımak gösterilmiştir [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) sınıfı.  
  
> [!NOTE]
>  Bu örnek yükseltirseniz sistemde yüklü olmasını gerektirir.  
  
 Adlı Visual Studio'da yeni bir WPF uygulaması projesi oluşturma **InkRecognition**. Window1.xaml dosyasının içeriğini aşağıdaki XAML kod ile değiştirin. Bu kod uygulamanın kullanıcı arabirimi işler.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 \Program Files\Microsoft Shared\Ink bulunabilir Microsoft.Ink.dll Microsoft Ink derlemesine başvuru ekleyin. Dosyanın arkasındaki kod içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
