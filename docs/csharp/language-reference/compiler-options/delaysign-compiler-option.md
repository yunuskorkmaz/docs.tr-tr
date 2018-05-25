---
title: -delaysign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# Derleyici Seçenekleri)

Bu seçenek, böylece bir dijital imza daha sonra eklenebilir çıktı dosyasında yer ayırmak için derleyici neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`

Kullanım **- delaysign-** tam imzalı bir derleme istiyorsanız. Kullanım **- delaysign +** yalnızca ortak anahtar derlemede yerleştirmek istiyorsanız. Varsayılan değer **- delaysign-**.

## <a name="remarks"></a>Açıklamalar

**- Delaysign** seçeneği hiçbir etkisi ile kullanılmadığı sürece [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) veya [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

**- Delaysign** ve **- publicsign** seçenekleri karşılıklı olarak birbirini dışlar.

Tam imzalı bir derleme istediğinde bildirimi (derleme meta verilerini) içeren ve karmayı özel anahtarıyla imzalar dosyayı derleyici karma hale getirir. Bu işlem bildirimini içeren dosyanın depolandığı bir dijital imza oluşturur. Bir derlemeyi imzalı gecikme olduğunda derleyici işlem değil ve daha sonra imzanın eklenmesi için imza ancak yer ayırır dosyasında depolamak.

Örneğin, kullanarak **- delaysign +** genel önbelleğinde derleme yerleştirilecek tester sağlar. Sınama sonra tam olarak derleme özel anahtarı kullanarak derlemeye koyarak oturum [derleme bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programı.

Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Açık **özellikleri** projesi için sayfa.
1. Değiştirme **gecikme yalnızca oturum** özelliği.

Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Ayrıca Bkz.

 [C# - publicsign seçeneği](publicsign-compiler-option.md)  
 [C# Derleyici Seçenekleri](index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
