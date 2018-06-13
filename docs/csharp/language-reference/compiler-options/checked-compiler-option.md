---
title: -checked (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4ed8467b0e1923aedf38edfd4a25414cbcb88b7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218318"
---
# <a name="-checked-c-compiler-options"></a>-checked (C# Derleyici Seçenekleri)
**-İşaretli** seçeneği belirtir ve veri türü, aralığın dışında bir değer sonuçlanan bir tamsayı aritmetiği deyimi kapsamında değil olup bir [işaretli](../../../csharp/language-reference/keywords/checked.md) veya [ Unchecked](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcük, bir çalışma zamanı özel neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsamında bir tamsayı aritmetiği deyimi bir `checked` veya `unchecked` anahtar sözcüğü etkisini tabi değil **-işaretli** seçeneği.  
  
 Kapsamında olmayan bir tamsayı aritmetik deyim, bir `checked` veya `unchecked` anahtar sözcüğü sonuçları veri türü aralık dışında bir değer ve **-checked +** (**-işaretli**) kullanılır derleme, bu deyim bir özel durum çalışma zamanında neden olur. Varsa **- işaretli -** kullanılan derlemede deyimi çalışma zamanında bir özel durum neden olmaz.  
  
 Bu seçenek için varsayılan değer **- işaretli -**. Kullanmak için bir senaryo **- işaretli -** büyük uygulamalar oluşturmaktır. Bazen otomatikleştirilmiş Araçlar, bu tür uygulamalar oluşturmak için kullanılır ve böyle bir araç otomatik olarak ayarlayabilir **-işaretli** için +. Belirterek aracın genel Varsayılanı geçersiz kılabilirsiniz **- işaretli -**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası. Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Tıklatın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **denetlemek için aritmetik taşma/underflow** özelliği.  
  
 Bu derleyici seçeneği programlı olarak erişmek için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut derlerken `t2.cs`. Kullanımını `-checked` komutunu herhangi bir tamsayı aritmetik deyimle dosyasında, kapsamında olduğunu belirten bir `checked` veya `unchecked` anahtar sözcüğü ve bu veri türü aralık dışında bir değer sonuçlarında neden olan bir özel durum çalışma süre.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
