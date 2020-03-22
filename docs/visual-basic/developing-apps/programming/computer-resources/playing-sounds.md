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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345516"
---
# <a name="playing-sounds-visual-basic"></a>Ses Çalma [Visual Basic]

Nesne `My.Computer.Audio` sesleri çalmak için yöntemler sağlar.  
  
## <a name="playing-sounds"></a>Ses Çalma  

 Arka plan çalma, ses çalarken uygulamanın diğer kodu yürütmesini sağlar. Yöntem, `My.Computer.Audio.Play` uygulamanın aynı anda yalnızca bir arka plan sesi çatlamasına olanak tanır; uygulama yeni bir arka plan sesi çaldığında, önceki arka plan sesini çalmayı durdurur. Ayrıca bir ses çalabilir ve tamamlanmasını bekleyebilirsiniz.  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntem bir ses çalar. Belirtildiğinde, `AudioPlayMode.WaitToComplete` `My.Computer.Audio.Play` arama kodu devam etmeden önce ses tamamlanana kadar bekler. Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir .wav ses dosyasına atıfta bulunduğundan emin olmalısınız  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntem bir ses çalar. Bu örneği kullanırken, uygulama kaynaklarının Şelale adlı bir .wav ses dosyası içerdiğinden emin olmalısınız.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Döngü Sesleri Oynatma  

 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntem belirtildiği nde `PlayMode.BackgroundLoop` arka planda belirtilen sesi çalar. Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir .wav ses dosyasına atıfta bulunduğundan emin olmalısınız.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntem belirtildiği nde `PlayMode.BackgroundLoop` arka planda belirtilen sesi çalar. Bu örneği kullanırken, uygulama kaynaklarının Şelale adlı bir .wav ses dosyası içerdiğinden emin olmalısınız.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Önceki kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet picker, Windows Forms **Uygulamalar > Ses**bulunur. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
 Genel olarak, bir uygulama bir döngü sesi çaldığında, sonunda sesi durdurmalıdır.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Arka Plandaki Seslerin Ç9latını Durdurma  

 Uygulamanın `My.Computer.Audio.Stop` şu anda çalan arka planı veya döngü sesini durdurmak için yöntemi kullanın.  
  
 Genel olarak, bir uygulama bir döngü sesi çaldığında, bir noktada sesi durdurmalıdır.  
  
 Aşağıdaki örnek, arka planda çalan bir sesi durdurur.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Önceki kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet picker, Windows Forms **Uygulamalar > Ses**bulunur. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
## <a name="playing-system-sounds"></a>Çalma Sistemi Sesleri  

 Belirtilen `My.Computer.Audio.PlaySystemSound` sistem sesini çalmak için yöntemi kullanın.  
  
 Yöntem, `My.Computer.Audio.PlaySystemSound` <xref:System.Media.SystemSound> sınıftan paylaşılan üyelerden biri bir parametre olarak alır. Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.  
  
 Aşağıdaki örnekte `My.Computer.Audio.PlaySystemSound` bir sistem sesi çalmak için yöntem kullanır.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
