---
title: 'Nasıl yapılır: Çözümleme İpuçları ile Mürekkep Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
ms.openlocfilehash: a4c38ddf52e9054fe9126df4b7e172548617b90d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375486"
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a>Nasıl yapılır: Çözümleme İpuçları ile Mürekkep Çözümleme
Bir [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) bir ipucu sağlar [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) bağlı olduğu için.  İpucu tarafından belirtilen alan uygulandığı [System.Windows.Ink.ContextNode.Location%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594508(v=vs.90)) özelliği [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) ve mürekkep Çözümleyicisi için ek bağlam sağlar tanıma doğruluğu artırır. [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) ipucu alanı içinde alınan mürekkep çözümleme bu bağlam bilgilerini uygulanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok kullanan bir uygulamayı [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) nesneler üzerinde mürekkep girişi kabul eden form. Uygulamanın kullandığı [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594341(v=vs.90)) özelliği, formdaki her giriş için bağlam bilgilerini sağlar.  Uygulama, arka plan analizi mürekkep çözümleme için kullanır ve tüm form beş saniye sonra kullanıcının mürekkep eklemeyi durdurur temizler.  
  
 [!code-xaml[HowToAnalyzeInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
