---
title: Ses Çalma
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345516"
---
# <a name="playing-sounds-visual-basic"></a>Ses Çalma [Visual Basic]

`My.Computer.Audio` nesnesi, ses çalmak için yöntemler sağlar.  
  
## <a name="playing-sounds"></a>Ses Çalma  

 Arka planda yürütme, ses çalarken uygulamanın diğer kodu yürütmesini sağlar. `My.Computer.Audio.Play` yöntemi, uygulamanın tek seferde yalnızca bir arka plan sesi oynamasını sağlar; uygulama yeni bir arka plan sesi yürüttüğünde, önceki arka plan sesinin çalınmasını bırakır. Ayrıca bir ses oynatabilir ve tamamlanmasını bekleyebilirsiniz.  
  
 Aşağıdaki örnekte `My.Computer.Audio.Play` yöntemi bir ses oynar. `AudioPlayMode.WaitToComplete` belirtildiğinde, kod çağrılmadan önce `My.Computer.Audio.Play` ses tamamlanana kadar bekler. Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 Aşağıdaki örnekte `My.Computer.Audio.Play` yöntemi bir ses oynar. Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Döngü seslerini oynama  

 Aşağıdaki örnekte, `PlayMode.BackgroundLoop` belirtildiğinde `My.Computer.Audio.Play` yöntemi belirtilen sesi arka planda yürütür. Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 Aşağıdaki örnekte, `PlayMode.BackgroundLoop` belirtildiğinde `My.Computer.Audio.Play` yöntemi belirtilen sesi arka planda yürütür. Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **Windows Forms uygulamalarda > Ses**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, sonunda sesi durdurmanız gerekir.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Arka planda seslerin çalınmasını durdurma  

 Uygulamanın Şu anda yürütülmekte olan arka plan veya döngü sesini durdurmak için `My.Computer.Audio.Stop` yöntemini kullanın.  
  
 Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, bir noktada sesi durdurmalıdır.  
  
 Aşağıdaki örnek, arka planda oynatılan bir sesi sonlandırır.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **Windows Forms uygulamalarda > Ses**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Sistem seslerini oynama  

 Belirtilen sistem sesini çalmak için `My.Computer.Audio.PlaySystemSound` yöntemini kullanın.  
  
 `My.Computer.Audio.PlaySystemSound` yöntemi, <xref:System.Media.SystemSound> sınıfından paylaşılan üyelerden birini parametre olarak alır. Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.  
  
 Aşağıdaki örnekte, bir sistem sesini çalmak için `My.Computer.Audio.PlaySystemSound` yöntemi kullanılmaktadır.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
