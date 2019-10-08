---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 3da049b912d791f26814bb4b6cbb70998803726a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005641"
---
# <a name="-doc"></a>-doc
Belge açıklamalarını bir XML dosyasına işler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-doc[+ | -]  
```

veya  

```console
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. \+ Veya yalnızca `-doc` belirtildiğinde, derleyicinin belge bilgilerini oluşturup bir XML dosyasına yerleştirmesini sağlar. @No__t-0 ' ı belirtmek, `-doc` Belirtmemeye değil, hiçbir belge bilgisinin oluşturulmamasına neden olan eşdeğerdir.|  
|`file`|@No__t-0 kullanılırsa gereklidir. Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan çıkış XML dosyasını belirtir. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 seçeneği, derleyicinin belge açıklamalarını içeren bir XML dosyası oluşturup oluşturmayacağını denetler. @No__t-0 sözdizimini kullanırsanız, `file` parametresi, XML dosyasının adını belirtir. @No__t-0 veya `-doc+` kullanırsanız, derleyici XML dosya adını derleyicinin oluşturmakta olduğu yürütülebilir dosya veya kitaplıktan alır. @No__t-0 kullanırsanız veya `-doc` seçeneğini belirtmezseniz, derleyici bir XML dosyası oluşturmaz.  
  
 Kaynak kodu dosyalarında, belge açıklamaları aşağıdaki tanımlardan önce olabilir:  
  
- Bir [sınıf](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirim](../../../visual-basic/language-reference/statements/interface-statement.md) gibi Kullanıcı tanımlı türler  
  
- Alan, [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özellik](../../../visual-basic/language-reference/statements/property-statement.md), [işlev](../../../visual-basic/language-reference/statements/function-statement.md)veya alt [yordam](../../../visual-basic/language-reference/statements/sub-statement.md)gibi Üyeler.  
  
 Oluşturulan XML dosyasını Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle birlikte kullanmak IÇIN, XML dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin. XML dosyasının derlemeyle aynı dizinde olduğundan emin olun; böylece derlemeye Visual Studio projesinde başvuruluyorsa,. xml dosyası da bulunur. IntelliSense 'in bir proje içinde veya bir proje tarafından başvurulan projelerde kod için çalışması için XML belge dosyaları gerekli değildir.  
  
 @No__t-0 ile derlemediğiniz takdirde, XML dosyası `<assembly></assembly>` etiketlerini içerir. Bu Etiketler, derlemenin çıkış dosyası için derleme bildirimini içeren dosyanın adını belirtir.  
  
 Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/index.md) .  
  
|Visual Studio tümleşik geliştirme ortamında belge ayarlamak için|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **XML belgesi oluştur dosyası** kutusunda değeri ayarlayın.|  
  
## <a name="example"></a>Örnek  
 Bkz. bir örnek için [kodunuzu XML Ile belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
