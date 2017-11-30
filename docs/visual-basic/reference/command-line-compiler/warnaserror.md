---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04b79b3d14a9c4a9f9721860cd1ed44032dfa5d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
Derleyicinin birinci bir uyarı hata olarak ele almasını neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|+ &#124; -|İsteğe bağlı. Varsayılan olarak, `/warnaserror-` olan etkili; uyarılar derleyici çıktı dosyası üretmeyi engellemez. `/warnaserror` Aynı seçeneği olarak `/warnaserror+`, hata olarak kabul edilmesi uyarıları oluşturulmasına neden olur.|  
|`numberList`|İsteğe bağlı. Uyarı Kimliği virgülle ayrılmış listesi olduğu numaraları `/warnaserror` seçeneği uygulanır. Hiçbir uyarı kimliği belirtilmezse, `/warnaserror` seçenek, tüm uyarıları için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `/warnaserror` Seçeneği tüm uyarıları hata olarak değerlendirir. Uyarılar yerine hata olarak bildirilen normalde bildirilen iletiler. Derleyici uyarıları olarak aynı uyarı sonraki oluşumlarını bildirir.  
  
 Varsayılan olarak, `/warnaserror-` yalnızca vericidir uyarıların neden olur, etkilidir. `/warnaserror` Aynı seçeneği olarak `/warnaserror+`, hata olarak kabul edilmesi uyarıları oluşturulmasına neden olur.  
  
 Hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları istiyorsanız, hata olarak değerlendirmek için uyarı numaralarını virgülle ayrılmış bir listesini belirtebilirsiniz.  
  
> [!NOTE]
>  `/warnaserror` Seçeneği denetlemez nasıl uyarılar görüntülenir. Kullanım [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) uyarılarını devre dışı bırakma seçeneği.  
  
|Tüm uyarıları Visual Studio IDE içinde hata olarak ele almasını/warnaserror ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Tıklatın **derleme** sekmesi.<br />3.  Emin olun **tüm uyarıları devre dışı bırakmak** onay kutusunu olarak işaretli.<br />4.  Denetleme **tüm uyarıları hata ele** onay kutusu.|  
  
|/ Warnaserror belirli uyarıları Visual Studio IDE içinde hata olarak ele almasını ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.<br />2.  Tıklatın **derleme** sekmesi.<br />3.  Emin olun **tüm uyarıları devre dışı bırakmak** onay kutusunu olarak işaretli.<br />4.  Emin olun **tüm uyarıları hata ele** onay kutusunu olarak işaretli.<br />5.  Seçin **hata** gelen **bildirim** hata olarak kabul uyarı bitişik sütun.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve birinci bulduğu her uyarı için bir hata görüntülenecek derleyici yönlendirir.  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve yalnızca kullanılmayan yerel değişkenler (42024) için uyarıyı hata olarak kabul eder.  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Visual Basic'te uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic)
