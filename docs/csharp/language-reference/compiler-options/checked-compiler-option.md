---
title: "-checked (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e02f82bb0dd2952bd2f192af7ff233194a045619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-compiler-options"></a>/checked (C# Derleyici Seçenekleri)
**/ Checked** seçeneği belirtir ve veri türü, aralığın dışında bir değer sonuçlanan bir tamsayı aritmetiği deyimi kapsamında değil olup bir [işaretli](../../../csharp/language-reference/keywords/checked.md) veya [ Unchecked](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcük, bir çalışma zamanı özel neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsamında bir tamsayı aritmetiği deyimi bir `checked` veya `unchecked` anahtar sözcüğü etkisini tabi değil **/ checked** seçeneği.  
  
 Kapsamında olmayan bir tamsayı aritmetik deyim, bir `checked` veya `unchecked` anahtar sözcüğü sonuçları veri türü aralık dışında bir değer ve **/ checked +** (**/ checked**) kullanılır derleme, bu deyim bir özel durum çalışma zamanında neden olur. Varsa **/ checked-** kullanılan derlemede deyimi çalışma zamanında bir özel durum neden olmaz.  
  
 Bu seçenek için varsayılan değer **/ checked-**. Kullanmak için bir senaryo **/ checked-** büyük uygulamalar oluşturmaktır. Bazen otomatikleştirilmiş Araçlar, bu tür uygulamalar oluşturmak için kullanılır ve böyle bir araç otomatik olarak ayarlayabilir **/ checked** için +. Belirterek aracın genel Varsayılanı geçersiz kılabilirsiniz **/ checked-**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası. Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Tıklatın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **denetlemek için aritmetik taşma/underflow** özelliği.  
  
 Bu derleyici seçeneği programlı olarak erişmek için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut derlerken `t2.cs`. Kullanımını `/checked` komutunu herhangi bir tamsayı aritmetik deyimle dosyasında, kapsamında olduğunu belirten bir `checked` veya `unchecked` anahtar sözcüğü ve bu veri türü aralık dışında bir değer sonuçlarında neden olan bir özel durum çalışma süre.  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
