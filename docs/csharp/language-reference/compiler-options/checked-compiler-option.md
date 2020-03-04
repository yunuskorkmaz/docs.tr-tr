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
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239698"
---
# <a name="-checked-c-compiler-options"></a>-Checked (C# derleyici seçenekleri)
**-Checked** seçeneği, veri türü aralığının dışında olan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) bir anahtar sözcüğünün kapsamında olmayan bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin bir çalışma zamanı özel durumuna neden olup olmadığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `checked` veya `unchecked` anahtar sözcüğünün kapsamındaki tamsayı aritmetik bir ifade, **-Checked** seçeneğinin etkisine tabi değildir.  
  
 Bir `checked` veya `unchecked` anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik bildirim, derlemede bir değer ve **-Checked +** (veya **-Checked**) kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olur. **-Checked-** derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olmaz.  
  
 Bu seçenek için varsayılan değer **-denetlenir-** ; taşma denetimi devre dışı.
 
 Bazen, büyük uygulamalar oluşturmak için kullanılan otomatikleştirilmiş araçlar + ' a ayarlanır. ' In kullanılmasına yönelik bir senaryo,-Checked-belirterek aracın genel varsayılanını geçersiz kılmalıdır.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın. Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Aritmetik taşma Için denetimi** değiştirin özelliği.  
  
 Bu derleyici seçeneğine program aracılığıyla erişmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut `t2.cs`derler. Komutunda `-checked` kullanımı, dosyasında bir `checked` veya `unchecked` anahtar sözcüğünün kapsamında olmayan herhangi bir tamsayı aritmetik deyimin olduğunu ve veri türünün aralığı dışında bir değer oluşmasına neden olur, çalışma zamanında bir özel duruma neden olur.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
