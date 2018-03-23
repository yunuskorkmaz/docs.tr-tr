---
title: -başvuru (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba879dd7079b35bea50c4a6c1d67da7aa57110f6
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-reference-visual-basic"></a>-başvuru (Visual Basic)
Belirtilen derlemelerde türü bilgileri şu anda derlediğiniz proje kullanılabilir hale getirmek derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`fileList`|Gerekli. Derleme dosya adlarının virgülle ayrılmış listesi. Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme meta verilerini içe aktardığınız dosyaları içermelidir. Yalnızca genel türleri dışında derleme görünür. [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçenek, bir modülden meta verileri alır.  
  
 Bir derlemeye (a derlemesi) başvurursanız kendisi başka bir derlemeye (B derlemesi) başvuran, varsa B derlemesine başvuru gerekir:  
  
-   Derlemesi türünden bir türden devralır veya derleme B'deki bir arabirimi uygular.  
  
-   Alan, özellik, olay veya b derlemesinden dönüş türü veya parametresi türü olan yöntemi çağrılır.  
  
 Kullanım [- LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için.  
  
 Derleyicinin türü derlemedeki (modülü değil) tanımak bu türü çözümlemeye zorlanması gerekir. Türünün bir örneği tanımlamak için nasıl Bunu yapmak için bir örnek verilmiştir. Diğer yolları derleyici için derlemeyi türü adları çözümlemek kullanılabilir. Örneğin, bir derlemede türünden devralan, tür adı sonra derleyiciye bilinir.  
  
 Başvuruları yaygın olarak kullanılan Vbc.rsp yanıt dosyası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler, varsayılan olarak kullanılır. Kullanmak `-noconfig` derleyicinin Vbc.rsp kullanmasını istemiyorsanız.  
  
 Kısa formunu `-reference` olan `/r`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu kaynak dosyasını derler `Input.vb` ve başvuru derlemelerden `Metad1.dll` ve `Metad2.dll` üretmek için `Out.exe`.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
