---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: c06326a250fba0de2f63e13672b4fffbfa8a07f0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835069"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)
Derleyici ilk geçtiği bir uyarı hata olarak değerlendirilecek neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|+ &#124; -|İsteğe bağlı. Varsayılan olarak, `-warnaserror-` olan etkin; uyarıları derleyicinin bir çıktı dosyası üretir gelen engellemez. `-warnaserror` Aynı olan seçenek olarak `-warnaserror+`, uyarıları hata olarak kabul edilmesine neden olur.|  
|`numberList`|İsteğe bağlı. Uyarı Kimliği virgülle ayrılmış listesi olduğu numaraları `-warnaserror` seçeneği uygular. Uyarı kimliği yok belirtilirse, `-warnaserror` seçenek, tüm uyarıları için geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-warnaserror` Seçeneği, tüm uyarıları hata olarak değerlendirir. Bunun yerine uyarıları hata olarak bildirilen gibi normalde bildirilebilecek iletiler. Derleyici karşılaşıldığında aynı uyarı uyarı olarak bildirir.  
  
 Varsayılan olarak, `-warnaserror-` uyarıları yalnızca bilgilendirici olması neden olur, etkilidir. `-warnaserror` Aynı olan seçenek olarak `-warnaserror+`, uyarıları hata olarak kabul edilmesine neden olur.  
  
 İsterseniz hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları hata olarak değerlendirilecek uyarıların virgülle ayrılmış bir listesini belirtebilirsiniz.  
  
> [!NOTE]
>  `-warnaserror` Seçeneği uyarıları nasıl görüntüleneceğini denetlemez. Kullanım [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) uyarıları devre dışı bırakma seçeneği.  
  
|-Tüm uyarıları Visual Studio IDE'deki hata olarak değerlendir warnaserror ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **derleme** sekmesi.<br />3.  Emin **tüm uyarıları devre dışı bırak** onay kutusu olarak işaretli değildir.<br />4.  Denetleme **tüm uyarıları hata olarak değerlendir** onay kutusu.|  
  
|-Belirli uyarıları Visual Studio IDE'deki hata olarak değerlendir warnaserror ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.<br />2.  Tıklayın **derleme** sekmesi.<br />3.  Emin **tüm uyarıları devre dışı bırak** onay kutusu olarak işaretli değildir.<br />4.  Emin **tüm uyarıları hata olarak değerlendir** onay kutusu olarak işaretli değildir.<br />5.  Seçin **hata** gelen **bildirim** hata olarak değerlendirilip uyarı bitişik sütun.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve bulduğu her uyarı ilk geçtiği yeri bulunmadığında hata gösterilecekse derleyici yönlendirir.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` ve yalnızca kullanılmayan yerel değişkenler (42024) için uyarı hata olarak değerlendirir.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic'teki Uyarıları Yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic)
