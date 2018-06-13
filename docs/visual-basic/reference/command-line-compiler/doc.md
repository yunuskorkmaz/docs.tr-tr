---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b64372d4b6063da85739e939bb33abd4650ecb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651563"
---
# <a name="-doc"></a>-doc
Belge açıklamaları bir XML dosyasına işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtme +, veya yalnızca `-doc`, belgeleri bilgileri oluşturmak ve bir XML dosyasında yerleştirmek derleyici neden olur. Belirtme `-` değil belirtme eşdeğerdir `-doc`, hiçbir belge bilgiler oluşturulmasına neden.|  
|`file`|Gerekli olursa `-doc:` kullanılır. Derleme kaynak kodu dosyaları açıklamalardan doldurulur çıkış XML dosyasının belirtir. Dosya adı boşluk içeriyorsa adı tırnak işaretleri çevreleyen ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 `-doc` Derleyici belge açıklamaları içeren bir XML dosyası oluşturur olup olmadığını kontrol eder seçeneği. Kullanırsanız `-doc:file` sözdizimi, `file` parametresi, XML dosyasının adını belirtir. Kullanırsanız `-doc` veya `-doc+`, derleyici XML dosya adı yürütülebilir dosya veya derleyici oluşturma kitaplığından alır. Kullanırsanız `-doc-` veya belirtmeyin `-doc` seçeneği, derleyici bir XML dosyası oluşturmaz.  
  
 Kaynak kodu dosyaları belge açıklamaları aşağıdaki tanımları koyun:  
  
-   Kullanıcı tanımlı türleri, aşağıdaki gibi bir [sınıfı](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Bir alan gibi üyeleri [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özelliği](../../../visual-basic/language-reference/statements/property-statement.md), [işlevi](../../../visual-basic/language-reference/statements/function-statement.md), veya [alt yordama](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Visual Studio ile oluşturulan XML dosyasını kullanmak için [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, desteklemek istediğiniz derleme ile aynı olması, XML dosyasının dosya adı sağlar. Böylece Visual Studio projesini derleme başvurulduğunda .xml dosyası da bulunur derlemeyle aynı dizinde XML dosyası olduğundan emin olun. XML belge dosyalarını kod projesi tarafından başvurulan projeleri veya bir proje içinde çalışmak IntelliSense için gerekli değildir.  
  
 İle derleme sürece `/target:module`, etiketler XML dosyasını içeren `<assembly></assembly>`. Bu etiketler derleme çıktı dosyası için derleme bildirimi içeren dosyanın adını belirtin.  
  
 Bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) yolları belgeleri açıklamaları kodunuzda oluşturmak için.  
  
|Belge Visual Studio tümleşik geliştirme ortamı ayarlamak için-|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Değer kümesinde **oluşturmak XML belge dosyası** kutusu.|  
  
## <a name="example"></a>Örnek  
 Bkz: [kodunuzu belgeleme XML ile](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) bir örnek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
