---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f9d4f584f217e6996a499614b97f184b28664f8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="doc"></a>/doc
Belge açıklamaları bir XML dosyasına işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtme +, veya yalnızca `/doc`, belgeleri bilgileri oluşturmak ve bir XML dosyasında yerleştirmek derleyici neden olur. Belirtme `-` değil belirtme eşdeğerdir `/doc`, hiçbir belge bilgiler oluşturulmasına neden.|  
|`file`|Gerekli olursa `/doc:` kullanılır. Derleme kaynak kodu dosyaları açıklamalardan doldurulur çıkış XML dosyasının belirtir. Dosya adı boşluk içeriyorsa adı tırnak işaretleri çevreleyen ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 `/doc` Derleyici belge açıklamaları içeren bir XML dosyası oluşturur olup olmadığını kontrol eder seçeneği. Kullanırsanız `/doc:``file` sözdizimi, `file` parametresi, XML dosyasının adını belirtir. Kullanırsanız `/doc` veya `/doc+`, derleyici XML dosya adı yürütülebilir dosya veya derleyici oluşturma kitaplığından alır. Kullanırsanız `/doc-` veya belirtmeyin `/doc` seçeneği, derleyici bir XML dosyası oluşturmaz.  
  
 Kaynak kodu dosyaları belge açıklamaları aşağıdaki tanımları koyun:  
  
-   Kullanıcı tanımlı türleri, aşağıdaki gibi bir [sınıfı](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Bir alan gibi üyeleri [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özelliği](../../../visual-basic/language-reference/statements/property-statement.md), [işlevi](../../../visual-basic/language-reference/statements/function-statement.md), veya [alt yordama](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Oluşturulan XML dosyası ile kullanmak için [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, desteklemek istediğiniz derleme ile aynı olması, XML dosyasının dosya adı sağlar. XML dosyası derleme ile aynı dizinde böylece zaman derleme başvuru olduğundan emin olun [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] proje, .xml dosyasını da bulunduğunda. XML belge dosyalarını kod projesi tarafından başvurulan projeleri veya bir proje içinde çalışmak IntelliSense için gerekli değildir.  
  
 İle derleme sürece `/target:module`, etiketler XML dosyasını içeren `<assembly></assembly>`. Bu etiketler derleme çıktı dosyası için derleme bildirimi içeren dosyanın adını belirtin.  
  
 Bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) yolları belgeleri açıklamaları kodunuzda oluşturmak için.  
  
|Tümleşik geliştirme ortamı/doc Visual Studio'da ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Değer kümesinde **oluşturmak XML belge dosyası** kutusu.|  
  
## <a name="example"></a>Örnek  
 Bkz: [kodunuzu belgeleme XML ile](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) bir örnek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
