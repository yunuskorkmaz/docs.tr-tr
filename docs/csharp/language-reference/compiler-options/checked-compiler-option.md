---
title: -kontrol edildi (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cb4dbadfa4efd0750ffd3dea88a3f661e2f85a8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173776"
---
# <a name="-checked-c-compiler-options"></a>-kontrol edildi (C# Derleyici Seçenekleri)
**Denetlenen** seçenek, veri türünün kapsamı dışında bir değerle sonuçlanan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) anahtar kelime kapsamında olmayan bir tamsayı aritmetik deyiminin çalışma zamanı özel durum larına neden olup olmadığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir veya `checked` `unchecked` anahtar kelime kapsamında olan bir tamsayı aritmetik **deyimi- işaretli** seçeneğin etkisine tabi değildir.  
  
 Bir `checked` veya `unchecked` anahtar kelime kapsamında olmayan bir tamsayı aritmetik deyimi, veri türünün aralığı dışında bir değerle sonuçlanır ve **-denetlenmiş+** (veya **-denetlenmiş)** derlemede kullanılırsa, bu ifade çalışma zamanında özel bir özel durum oluşturur. **Derlemede -denetlenen-** kullanılırsa, bu deyim çalışma zamanında özel bir özel durum neden olmaz.  
  
 Bu seçeneğin varsayılan değeri **-işaretli-**; taşma denetimi devre dışı bırakılır.

 Bazen, büyük uygulamalar oluşturmak için kullanılan otomatik araçlar ayarlanır -+' olarak denetlenir. -denetlenen- kullanmak için bir senaryo, -denetlenmiş- belirterek aracın genel varsayılanGeçersiz kılmaktır.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın. Daha fazla bilgi için Bkz. [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. **Gelişmiş** düğmesini tıklatın.  
  
4. **Aritmetik taşma** özelliği için Denetimi değiştirin.  
  
 Bu derleyici seçeneğine programlı <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>olarak erişmek için bkz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut derler. `t2.cs` `-checked` Komutun kullanımı, dosyadaki bir `checked` veya `unchecked` anahtar kelime kapsamında olmayan herhangi bir tamsayı aritmetik deyiminin veri türünün kapsamı dışında bir değerle sonuçlandığını ve çalışma zamanında bir özel durum almasına neden olduğunu belirtir.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
