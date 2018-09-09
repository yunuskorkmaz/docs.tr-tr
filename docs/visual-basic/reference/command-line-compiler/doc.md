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
ms.openlocfilehash: 4c77d063d64354bf4693ce82509f36be9d2e5b0c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249081"
---
# <a name="-doc"></a>-doc
Belge yorumlarını bir XML dosyasına işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtme +, veya yalnızca `-doc`, derleyicinin belgelendirme bilgilerini oluşturmak ve bir XML dosyasında yerleştirin. Belirtme `-` eşdeğeri değildir belirtme `-doc`, oluşturulacak belge bilgi neden.|  
|`file`|Gerekli if `-doc:` kullanılır. Kaynak kodu dosyaları derleme açıklamalardan doldurulur çıkış XML dosyasını belirtir. Dosya adı boşluk içeriyorsa adı tırnak işaretleri ile çevreleyen ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 `-doc` Seçeneği denetimleri olmadığını derleyici içeren belge yorumlarını bir XML dosyası oluşturur. Kullanırsanız `-doc:file` söz dizimini `file` parametre XML dosyasının adını belirtir. Kullanırsanız `-doc` veya `-doc+`, derleyicinin XML dosya adı yürütülebilir dosya veya derleyici oluşturma kitaplığından alır. Kullanırsanız `-doc-` veya belirtmeyin `-doc` seçeneği, derleyicinin bir XML dosyası oluşturmaz.  
  
 Kaynak kodu dosyalarında belge açıklamaları aşağıdaki tanımları koyabilirsiniz:  
  
-   Kullanıcı tanımlı türleri, aşağıdaki gibi bir [sınıfı](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Bir alan gibi bir üye [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özelliği](../../../visual-basic/language-reference/statements/property-statement.md), [işlevi](../../../visual-basic/language-reference/statements/function-statement.md), veya [alt yordam](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Visual Studio ile oluşturulan XML dosyasını kullanmak için [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, desteklemek istediğiniz derleme ile aynı olması, XML dosyasının dosya adı sağlar. Visual Studio projesinde derlemeye başvurulduğundan, .xml dosyasını da bulunur, böylece XML dosyasını derleme olarak aynı dizinde olduğundan emin olun. XML belge dosyaları, IntelliSense, kod bir proje veya içinde bir proje tarafından başvurulan projeler için çalışması gerekli değildir.  
  
 Derleme sürece `/target:module`, etiket XML dosyasını içeren `<assembly></assembly>`. Bu etiketler, derleme çıktı dosyası için derleme bildirimini içeren dosya adını belirtin.  
  
 Bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/index.md) kodunuza yorumlar gelen belgeleri oluşturmak yöntemleri.  
  
|Ayarlanacak - doc Visual Studio tümleşik geliştirme ortamı|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**. <br />2.  Tıklayın **derleme** sekmesi.<br />3.  Değer kümesindeki **oluşturmak XML belge dosyası** kutusu.|  
  
## <a name="example"></a>Örnek  
 Bkz: [kodunuzu belgeleme XML ile](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) örneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
