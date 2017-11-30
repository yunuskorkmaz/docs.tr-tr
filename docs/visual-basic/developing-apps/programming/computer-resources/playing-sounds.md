---
title: "Ses Çalma [Visual Basic]"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be5cec634482bf99ddff4ff6b6af8e897c4909e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="playing-sounds-visual-basic"></a>Ses Çalma [Visual Basic]
`My.Computer.Audio` Nesne ses çalma için yöntemler sağlar.  
  
## <a name="playing-sounds"></a>Ses Çalma  
 Arka plan çalma sesi çalar sırada başka bir kod yürütmek uygulaması sağlar. `My.Computer.Audio.Play` Yöntemi yalnızca bir arka plan aynı anda ses çalınmaya uygulama sağlar; uygulama yeni bir arka plan ses yürütüldüğünde, önceki arka plan ses çalma durdurur. Ses çalma ve tamamlanmasını bekleyin.  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi ses çalar. Zaman `AudioPlayMode.WaitToComplete` belirtilirse, `My.Computer.Audio.Play` kodu çağırma devam etmeden önce ses tamamlanana kadar bekler. Bu örnek kullanırken, dosya adı bilgisayarınızda bulunan bir .wav ses dosyası başvurduğundan emin olun  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi ses çalar. Bu örnek kullanırken, uygulama kaynaklarını Waterfall adlı bir .wav ses dosyası eklediğinizden emin olun.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Döngü ses çalma  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi oynadığı belirtilen ses arka planda olduğunda `PlayMode.BackgroundLoop` belirtilir. Bu örnek kullanırken, dosya adı bilgisayarınızda bulunan bir .wav ses dosyası başvurduğu emin olmalısınız.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi oynadığı belirtilen ses arka planda olduğunda `PlayMode.BackgroundLoop` belirtilir. Bu örnek kullanırken, uygulama kaynaklarını Waterfall adlı bir .wav ses dosyası eklediğinizden emin olun.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 Önceki kod örneğinde bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Ses**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Bir uygulama döngü ses yürütüldüğünde, genel olarak, bu sonunda ses durdurmanız gerekir.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Arka planda ses çalma durdurma  
 Kullanım `My.Computer.Audio.Stop` yöntemi uygulamanın arka plan oynatılmakta veya sesi döngü durdurmak için.  
  
 Genel olarak, bir uygulama döngü ses yürütüldüğünde, ses, belirli bir noktada durdurmanız gerekir.  
  
 Aşağıdaki örnek, arka planda yürütülen ses durdurur.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 Önceki kod örneğinde bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Ses**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Sistem ses çalma  
 Kullanım `My.Computer.Audio.PlaySystemSound` belirtilen sistem ses çalınmaya yöntemi.  
  
 `My.Computer.Audio.PlaySystemSound` Yöntemi bir parametresinden paylaşılan üyelerinden biri olarak aldığı <xref:System.Media.SystemSound> sınıfı. Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.  
  
 Aşağıdaki örnek kullanır `My.Computer.Audio.PlaySystemSound` bir sistem ses çalınmaya yöntemi.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
