---
title: -delaysıgn (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400202"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysıgn (C# Derleyici Seçenekleri)

Bu seçenek, bir dijital imza daha sonra eklenebilir böylece çıkış dosyasına yer ayırmak derleyicinin neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`

Kullanım **- delaysign-** tam imzalı bir derleme istiyorsanız. Kullanım **- delaysign +** yalnızca derleme içinde ortak anahtar yerleştirmek istiyorsanız. Varsayılan değer **- delaysign-**.

## <a name="remarks"></a>Açıklamalar

**- Delaysıgn** seçeneği ile birlikte kullanılmadığı sürece hiçbir etkiye sahiptir [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) veya [- keycontaıner](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

**- Delaysıgn** ve **- publicsign** seçenekleri karşılıklı olarak birbirini dışlar.

Tam imzalı bir derleme istediğinizde; derleyici bildirimi (derleme meta verileri) içeren ve karmayı özel anahtarla imzalar dosyayı karma hale getirir. Bu işlem, bir dijital imza bildirimi içeren dosyada depolanan oluşturur. Bir derlemeyi gecikmeli imzalanmış olduğunda, derleyici işlem değil ve daha sonra imzanın eklenmesi için dosyada depolamak imzaya ancak ayırır.

Örneğin, kullanarak **- delaysign +** derlemeyi genel önbellek üzerine koymasına olanak sağlar. Test edildikten sonra tam olarak derlemeyi kullanarak bir derlemede özel anahtarı yerleştirerek kaydolabilirsiniz [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programı.

Daha fazla bilgi için [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Açık **özellikleri** proje sayfası.
1. Değiştirme **gecikme yalnızca oturum** özelliği.

Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# - publicsign seçeneği](publicsign-compiler-option.md)  
- [C# Derleyici Seçenekleri](index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
