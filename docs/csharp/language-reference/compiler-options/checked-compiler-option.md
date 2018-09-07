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
ms.openlocfilehash: cf6fa0e87654d0f9d61f34ea9b29ad80921a5720
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084861"
---
# <a name="-checked-c-compiler-options"></a>-checked (C# Derleyici Seçenekleri)
**-Kullanıma** seçeneği veri türü ve aralığı dışında bir değer sonuçlanır bir tamsayı aritmetik deyiminin kapsamı içinde olup olmadığını belirten bir [kullanıma](../../../csharp/language-reference/keywords/checked.md) veya [ denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcüğü, bir çalışma zamanı özel durumuna neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsamında olan bir tamsayı aritmetik deyimi bir `checked` veya `unchecked` anahtar sözcüğü etkisini tabi olmayan **-kullanıma** seçeneği.  
  
 Kapsamında olmayan bir tamsayı aritmetik deyimi, bir `checked` veya `unchecked` veri türünün aralığı dışında bir değer anahtar sözcükleri ve **-checked +** (veya **-kullanıma**) kullanılır deyimi bir özel durum çalışma zamanında neden derlemeyi. Varsa **- checked -** kullanılan derlemede deyimi çalışma zamanında bir özel durum neden olmaz.  
  
 Bu seçenek için varsayılan değerdir **- checked -**; taşma denetimini devre dışı bırakıldı.
 
 Büyük uygulamalar oluşturmak için kullanılan araçları bazı durumlarda, otomatik ayarlama - teslim +. -Checked - belirterek Aracı'nın genel varsayılan geçersiz kılmak için - checked - kullanmaya yönelik bir senaryodur.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası. Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Tıklayın **derleme** özellik sayfası.  
  
3.  Tıklayın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **aritmetik taşma ve alttaşmayı denetle** özelliği.  
  
 Bu derleyici seçeneğini program aracılığıyla erişmek için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut `t2.cs`. Kullanımını `-checked` komutunu dosyasındaki tüm tamsayı aritmetik ifadesi, kapsamı içinde olmadığını belirten bir `checked` veya `unchecked` anahtar sözcüğü ve bu veri türünün aralığı dışında bir değer sonuçlarında neden olan bir özel durum çalışma saat.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
