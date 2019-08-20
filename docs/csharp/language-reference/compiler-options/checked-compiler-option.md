---
title: -Checked (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606993"
---
# <a name="-checked-c-compiler-options"></a>-Checked (C# derleyici seçenekleri)
**-Checked** seçeneği, veri türü aralığının dışında olan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) bir anahtar sözcüğünün kapsamında olmayan bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin bir çalışma zamanı özel durumuna neden olup olmadığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `checked` Or`unchecked` anahtar sözcüğünün kapsamındaki bir tamsayı aritmetik bildirim, **-Checked** seçeneğinin etkisine tabi değildir.  
  
 `checked` Or`unchecked` anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik ifade, veri türü aralığı dışında bir değer ile sonuçlanır ve **-Checked +** (veya **-Checked**) derlemede kullanılırsa, bu ifade bir çalışma zamanında özel durum. **-Checked-** derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olmaz.  
  
 Bu seçenek için varsayılan değer **-denetlenir-** ; taşma denetimi devre dışı.
 
 Bazen, büyük uygulamalar oluşturmak için kullanılan otomatikleştirilmiş araçlar + ' a ayarlanır. ' In kullanılmasına yönelik bir senaryo,-Checked-belirterek aracın genel varsayılanını geçersiz kılmalıdır.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın. Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Aritmetik taşma/yetersiz** yer özelliğinin denetimini değiştirin.  
  
 Bu derleyici seçeneğine program aracılığıyla erişmek için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut derlenir `t2.cs`. Komutunda öğesinin `-checked` kullanımı, bir `checked` veya `unchecked` anahtar sözcüğünün kapsamında olmayan dosyada herhangi bir tamsayı aritmetik deyimin olduğunu ve veri türü aralığının dışında bir değer oluşmasına neden olduğunu belirtir ışınızda.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
