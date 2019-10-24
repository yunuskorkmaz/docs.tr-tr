---
title: -başvuru (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 8f144dbd9376f15ac92e283472dac786a6972045
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775599"
---
# <a name="-reference-visual-basic"></a>-başvuru (Visual Basic)
Derleyicinin, belirtilen derlemelerde bulunan tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-reference:fileList  
```

veya

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`fileList`|Gerekli. Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçeri aktardığınız dosya (ler) bütünleştirilmiş kod meta verisi içermelidir. Yalnızca ortak türler derleme dışında görünür. [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.  
  
 Kendisi başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvuruyorsa, şu durumlarda derleme B 'ye başvurmanız gerekir:  
  
- Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.  
  
- B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.  
  
 Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) kullanın.  
  
 Derleyicinin bir derlemede (modül değil) bir türü tanıması için, türün çözümlenmesinin zorunlu olması gerekir. Bunu nasıl yapabileceğiniz bir örnek, türün bir örneğini tanımlamaktır. Derleyici için bir derlemede tür adlarını çözümlemek için diğer yollar mevcuttur. Örneğin, derlemedeki bir türden devralma yaparsanız, tür adı derleyici tarafından bilinmiş olur.  
  
 Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyası varsayılan olarak kullanılır. Derleyicinin Vbc. rsp kullanmasını istemiyorsanız, `-noconfig` kullanın.  
  
 @No__t_0 kısa biçimi `/r`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, `Metad1.dll` ve `Metad2.dll` ' den `Out.exe` üretmek için kaynak dosyayı `Input.vb` ve başvuru derlemelerini derler.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
