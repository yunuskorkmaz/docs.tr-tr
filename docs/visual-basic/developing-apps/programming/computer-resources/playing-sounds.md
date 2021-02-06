---
description: 'Daha fazla bilgi edinin: sesleri oynatma (Visual Basic)'
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
ms.openlocfilehash: 247af8274108ca8374cf87e53aa2aaad8e5e736c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641518"
---
# <a name="playing-sounds-visual-basic"></a>Ses Çalma [Visual Basic]

`My.Computer.Audio`Nesnesi, ses çalmak için yöntemler sağlar.  
  
## <a name="playing-sounds"></a>Ses Çalma  

 Arka planda yürütme, ses çalarken uygulamanın diğer kodu yürütmesini sağlar. Yöntemi, uygulamanın tek seferde `My.Computer.Audio.Play` yalnızca bir arka plan sesi oynamasına izin verir; uygulama yeni bir arka plan sesi oynadığında, önceki arka plan sesini çalmayı bırakır. Ayrıca bir ses oynatabilir ve tamamlanmasını bekleyebilirsiniz.  
  
 Aşağıdaki örnekte `My.Computer.Audio.Play` Yöntem bir ses oynar. `AudioPlayMode.WaitToComplete`Belirtildiğinde, `My.Computer.Audio.Play` kod çağrılmadan önce ses tamamlanana kadar bekler. Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 Aşağıdaki örnekte `My.Computer.Audio.Play` Yöntem bir ses oynar. Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a>Döngü seslerini oynama  

 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi belirtildiğinde belirtilen sesi arka planda yürütür `PlayMode.BackgroundLoop` . Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız.  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi belirtildiğinde belirtilen sesi arka planda yürütür `PlayMode.BackgroundLoop` . Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **Windows Forms uygulamalarda > ses** bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, sonunda sesi durdurmanız gerekir.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Arka planda seslerin çalınmasını durdurma  

 `My.Computer.Audio.Stop`Uygulamanın Şu anda yürütülmekte olan arka plan veya döngü sesini durdurmak için yöntemini kullanın.  
  
 Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, bir noktada sesi durdurmalıdır.  
  
 Aşağıdaki örnek, arka planda oynatılan bir sesi sonlandırır.  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **Windows Forms uygulamalarda > ses** bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Sistem seslerini oynama  

 `My.Computer.Audio.PlaySystemSound`Belirtilen sistem sesini çalmak için yöntemini kullanın.  
  
 `My.Computer.Audio.PlaySystemSound`Yöntemi, sınıfından paylaşılan üyelerden birini parametre olarak alır <xref:System.Media.SystemSound> . Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hata gösterir.  
  
 Aşağıdaki örnek, `My.Computer.Audio.PlaySystemSound` bir sistem sesini çalmak için yöntemini kullanır.  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
