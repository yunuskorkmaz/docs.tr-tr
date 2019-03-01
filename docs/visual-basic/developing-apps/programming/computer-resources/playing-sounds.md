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
ms.openlocfilehash: 56b156545fac2aba09d32139fdaad26da711e018
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966222"
---
# <a name="playing-sounds-visual-basic"></a>Ses Çalma [Visual Basic]
`My.Computer.Audio` Nesne sesleri çalmak için yöntemler sağlar.  
  
## <a name="playing-sounds"></a>Ses Çalma  
 Arka planda yürütmeyi uygulamanın ses çalar sırasında diğer kod yürütmesine olanak tanır. `My.Computer.Audio.Play` Yöntemi uygulamanın aynı anda yalnızca bir arka plan sesli sağlar; uygulamanın yeni bir arka plan ses yürütüldüğünde, önceki arka plan ses yürütmeyi durdurur. Ayrıca, bir ses çal ve tamamlanmasını bekleyin.  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi bir ses çalar. Zaman `AudioPlayMode.WaitToComplete` belirtilen `My.Computer.Audio.Play` kodu çağırma devam etmeden önce sesi tamamlanana kadar bekler. Bu örnek kullanırken, dosya adı bilgisayarınızda .wav ses dosyası başvurduğundan emin olun  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi bir ses çalar. Bu örnek kullanırken, uygulama kaynaklarının Şelale adlı .wav ses dosyası eklediğinizden emin olun.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Döngü ses çalma  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi arka planda belirtilen ses çalar olduğunda `PlayMode.BackgroundLoop` belirtilir. Bu örnek kullanırken, dosya adı bilgisayarınızda .wav ses dosyasına başvuruyor emin olmanız gerekir.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi arka planda belirtilen ses çalar olduğunda `PlayMode.BackgroundLoop` belirtilir. Bu örnek kullanırken, uygulama kaynaklarının Şelale adlı .wav ses dosyası eklediğinizden emin olun.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Yukarıdaki kod örneğinde, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Ses**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Genel olarak, bir uygulama dönen bir ses yürütüldüğünde, ses sonunda durdurmak.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Ses arka planda yürütmeyi durdurma  
 Kullanım `My.Computer.Audio.Stop` uygulamanın şu anda arka plan yürütme ya da ses döngü durdurmak için yöntemi.  
  
 Genel olarak, bir uygulama dönen bir ses yürütüldüğünde, belirli bir noktada sesi durdurmanız gerekir.  
  
 Aşağıdaki örnek, arkaplanda çalan bir sesi durdurur.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Yukarıdaki kod örneğinde, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Ses**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Sistem ses çalma  
 Kullanım `My.Computer.Audio.PlaySystemSound` sisteme ses çal için yöntemi.  
  
 `My.Computer.Audio.PlaySystemSound` Yöntemi alır bir parametre olarak paylaşılan üyelerinden <xref:System.Media.SystemSound> sınıfı. Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.  
  
 Aşağıdaki örnekte `My.Computer.Audio.PlaySystemSound` bir sistem ses çal için yöntemi.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
