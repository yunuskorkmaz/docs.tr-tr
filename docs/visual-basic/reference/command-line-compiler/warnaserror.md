---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351704"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)
Derleyicinin bir uyarının ilk oluşumunu hata olarak ele almasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|+ &#124;-|İsteğe bağlı. Varsayılan `-warnaserror-` olarak etkindir; Uyarılar derleyicinin bir çıkış dosyası üretmasını engellemez. İle `-warnaserror` `-warnaserror+`aynı olan seçeneği, uyarıların hata olarak işlenmesine neden olur.|  
|`numberList`|İsteğe bağlı. `-warnaserror` Seçeneğin UYGULANDıĞı uyarı kimliği numaralarının virgülle ayrılmış listesi. Hiçbir uyarı KIMLIĞI belirtilmemişse, bu `-warnaserror` seçenek tüm uyarılar için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-warnaserror` Seçeneği tüm uyarıları hata olarak değerlendirir. Normalde uyarı olarak bildirilen tüm iletiler, bunun yerine hata olarak bildirilir. Derleyici aynı uyarının sonraki tekrarlamalarını uyarılarla bildirir.  
  
 Varsayılan olarak, `-warnaserror-` uyarıların yalnızca bilgilendirici olmasına neden olan, etkin olur. İle `-warnaserror` `-warnaserror+`aynı olan seçeneği, uyarıların hata olarak işlenmesine neden olur.  
  
 Yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz.  
  
> [!NOTE]
> Bu `-warnaserror` seçenek uyarıların nasıl görüntülendiğini denetlemez. Uyarıları devre dışı bırakmak için [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) seçeneğini kullanın.  
  
|Visual Studio IDE 'de tüm uyarıları hata olarak değerlendirmek için-warnaserror öğesini ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **tüm uyarıları devre dışı bırak** onay kutusunun işaretinin kaldırıldığından emin olun.<br />4. **tüm uyarıları hata olarak işle** onay kutusunu işaretleyin.|  
  
|Visual Studio IDE 'de belirli uyarıları hata olarak değerlendirmek için-warnaserror 'yi ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.<br />2. **Derle** sekmesine tıklayın.<br />3. **tüm uyarıları devre dışı bırak** onay kutusunun işaretinin kaldırıldığından emin olun.<br />4. **tüm uyarıları hata olarak işle** onay kutusunun işaretinin kaldırıldığından emin olun.<br />5. hata olarak değerlendirilmesi gereken uyarıya bitişik **bildirim** sütunundan **hata** seçin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, derleyicisini derler `In.vb` ve bulduğu her uyarının ilk oluşumu için bir hata görüntüleyecek şekilde yönlendirir.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir `T2.vb` hata olarak yalnızca kullanılmayan yerel değişkenler (42024) için uyarıyı derler ve değerlendirir.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic'teki Uyarıları Yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic)
