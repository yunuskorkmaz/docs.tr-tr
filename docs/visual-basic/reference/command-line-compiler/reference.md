---
title: /reference (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8c6851802afa818cc80b3f6d7eafc2ef47ac689
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-visual-basic"></a>/reference (Visual Basic)
Belirtilen derlemelerde türü bilgileri şu anda derlediğiniz proje kullanılabilir hale getirmek derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
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
  
 Kullanım [/Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için.  
  
 Derleyicinin türü derlemedeki (modülü değil) tanımak bu türü çözümlemeye zorlanması gerekir. Türünün bir örneği tanımlamak için nasıl Bunu yapmak için bir örnek verilmiştir. Diğer yolları derleyici için derlemeyi türü adları çözümlemek kullanılabilir. Örneğin, bir derlemede türünden devralan, tür adı sonra derleyiciye bilinir.  
  
 Başvuruları yaygın olarak kullanılan Vbc.rsp yanıt dosyası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler, varsayılan olarak kullanılır. Kullanmak `/noconfig` derleyicinin Vbc.rsp kullanmasını istemiyorsanız.  
  
 Kısa formunu `/reference` olan `/r`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kaynak dosyasını derler `Input.vb` ve başvuru derlemelerden `Metad1.dll` ve `Metad2.dll` üretmek için `Out.exe`.  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Ortak](../../../visual-basic/language-reference/modifiers/public.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
