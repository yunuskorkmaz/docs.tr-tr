---
title: Ses Çalma [Visual Basic]
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
ms.openlocfilehash: f303687fb86e23191727df769af52811a93fe71e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715796"
---
# <a name="playing-sounds-visual-basic"></a>Ses Çalma [Visual Basic]
`My.Computer.Audio` Nesne sesleri çalmak için yöntemler sağlar.  
  
## <a name="playing-sounds"></a>Ses Çalma  
 Arka planda yürütmeyi uygulamanın ses çalar sırasında diğer kod yürütmesine olanak tanır. `My.Computer.Audio.Play` Yöntemi uygulamanın aynı anda yalnızca bir arka plan sesli sağlar; uygulamanın yeni bir arka plan ses yürütüldüğünde, önceki arka plan ses yürütmeyi durdurur. Ayrıca, bir ses çal ve tamamlanmasını bekleyin.  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi bir ses çalar. Zaman `AudioPlayMode.WaitToComplete` belirtilen `My.Computer.Audio.Play` kodu çağırma devam etmeden önce sesi tamamlanana kadar bekler. Bu örnek kullanırken, dosya adı bilgisayarınızda .wav ses dosyası başvurduğundan emin olun  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi bir ses çalar. Bu örnek kullanırken, uygulama kaynaklarının Şelale adlı .wav ses dosyası eklediğinizden emin olun.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Döngü ses çalma  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi arka planda belirtilen ses çalar olduğunda `PlayMode.BackgroundLoop` belirtilir. Bu örnek kullanırken, dosya adı bilgisayarınızda .wav ses dosyasına başvuruyor emin olmanız gerekir.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi arka planda belirtilen ses çalar olduğunda `PlayMode.BackgroundLoop` belirtilir. Bu örnek kullanırken, uygulama kaynaklarının Şelale adlı .wav ses dosyası eklediğinizden emin olun.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 Yukarıdaki kod örneğinde, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Ses**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Genel olarak, bir uygulama dönen bir ses yürütüldüğünde, ses sonunda durdurmak.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Ses arka planda yürütmeyi durdurma  
 Kullanım `My.Computer.Audio.Stop` uygulamanın şu anda arka plan yürütme ya da ses döngü durdurmak için yöntemi.  
  
 Genel olarak, bir uygulama dönen bir ses yürütüldüğünde, belirli bir noktada sesi durdurmanız gerekir.  
  
 Aşağıdaki örnek, arkaplanda çalan bir sesi durdurur.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 Yukarıdaki kod örneğinde, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Ses**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Sistem ses çalma  
 Kullanım `My.Computer.Audio.PlaySystemSound` sisteme ses çal için yöntemi.  
  
 `My.Computer.Audio.PlaySystemSound` Yöntemi alır bir parametre olarak paylaşılan üyelerinden <xref:System.Media.SystemSound> sınıfı. Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.  
  
 Aşağıdaki örnekte `My.Computer.Audio.PlaySystemSound` bir sistem ses çal için yöntemi.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
