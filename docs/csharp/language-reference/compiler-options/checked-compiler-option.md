---
description: -Checked (C# derleyici seçenekleri)
title: -Checked (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: c92ad61b2f482631230e0e6aeb0af5716a4fcb61
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196838"
---
# <a name="-checked-c-compiler-options"></a>-Checked (C# derleyici seçenekleri)

**-Checked** seçeneği, veri türü aralığının dışında olan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) bir anahtar sözcüğünün kapsamında olmayan bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin bir çalışma zamanı özel durumuna neden olup olmadığını belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Or anahtar sözcüğünün kapsamındaki bir tamsayı aritmetik bildirim, `checked` `unchecked` **-Checked** seçeneğinin etkisine tabi değildir.  
  
 Bir veya anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik ifade, `checked` `unchecked` veri türü aralığı dışındaki bir değer ile sonuçlanır ve **-Checked +** (veya **-Checked**) derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olur. **-Checked-** derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olmaz.  
  
 Bu seçenek için varsayılan değer **-denetlenir-**; taşma denetimi devre dışı.

 Bazen, büyük uygulamalar oluşturmak için kullanılan otomatikleştirilmiş araçlar + ' a ayarlanır. ' In kullanılmasına yönelik bir senaryo,-Checked-belirterek aracın genel varsayılanını geçersiz kılmalıdır.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın. Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Aritmetik taşma Için denetimi** değiştirin özelliği.  
  
 Bu derleyici seçeneğine program aracılığıyla erişmek için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> ..  
  
## <a name="example"></a>Örnek  

 Aşağıdaki komut derlenir `t2.cs` . Komutunda öğesinin kullanımı `-checked` , bir veya anahtar sözcüğünün kapsamında olmayan, dosyadaki tüm tamsayı aritmetik deyimlerine `checked` `unchecked` ve veri türü aralığının dışında bir değer oluşmasına neden olur, çalışma zamanında bir özel duruma neden olur.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
