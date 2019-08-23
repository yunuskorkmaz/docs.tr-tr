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
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956526"
---
# <a name="handwriting-recognition"></a>El Yazısı Tanıma
Bu bölümde, WPF platformunda dijital mürekkeple ilgili olarak tanımanın temelleri ele alınmaktadır.  
  
## <a name="recognition-solutions"></a>Tanıma çözümleri  
 Aşağıdaki örnek, [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) sınıfını kullanarak mürekkebin nasıl tanınacağını göstermektedir.  
  
> [!NOTE]
> Bu örnek, el yazısı tanıyıcılarının sistemde yüklü olmasını gerektirir.  
  
 Visual Studio 'da **ınktanıması**adlı yenı bir WPF uygulaması projesi oluşturun. Window1. xaml dosyasının içeriğini aşağıdaki XAML kodu ile değiştirin. Bu kod, uygulamanın kullanıcı arabirimini işler.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 \Program Files\Common Files\Microsoft Shared\ınk' te bulunan Microsoft Ink derlemesine (Microsoft. Ink. dll) bir başvuru ekleyin. Arka plan kod dosyasının içeriğini aşağıdaki kodla değiştirin.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
