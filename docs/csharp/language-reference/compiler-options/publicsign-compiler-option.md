---
title: -publicsign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: ec25f9c1f2ef943db41bcfa20c8efd1d05866acd
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472854"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (C# Derleyici Seçenekleri)

Bu seçenek bir ortak anahtar uygulamak derleyici neden olur, ancak gerçekte derlemeyi imzalamak değil. **- Publicsign** seçeneğini de ayarlar bir bit çalışma zamanı dosyası gerçekten imzalanmış söyler derlemede.

## <a name="syntax"></a>Sözdizimi

```console
-publicsign
```

## <a name="arguments"></a>Arguments

Yok.

## <a name="remarks"></a>Açıklamalar

**- Publicsign** seçeneği kullanılmasını gerektiren [- keyfile](keyfile-compiler-option.md) veya [- keycontainer](keycontainer-compiler-option.md). **Keyfile** veya **keycontainer** seçenekleri ortak anahtarı belirtin.

**- Publicsign** ve **- delaysign** seçenekleri karşılıklı olarak birbirini dışlar.

Bazen "sahte oturum" veya "OSS işareti" olarak adlandırılan, ortak imzalama çıkış bütünleştirilmiş ortak anahtarı içerir ve "imzalı" bayrağını ayarlar, ancak gerçekte derleme özel bir anahtarla oturum değil. Bu kişiler yayımlanan "tam olarak imzalanmamış" derlemeler ile uyumludur, ancak derlemeler imzalamak için kullanılan özel anahtarı erişiminiz yoksa derlemeleri oluşturmak istediğiniz yere açık kaynak projeler için yararlıdır. Neredeyse hiçbir tüketicileri derleme tam olarak imzalanmamış denetlemek gerçekten gerekli olduğundan, bu genel olarak derlemeleri yerleşik burada tam olarak imzalanmış bir kullanılan neredeyse her senaryoda kullanışlı.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Açık **özellikleri** projesi için sayfa.
1. Değiştirme **gecikme yalnızca oturum** özelliği.

## <a name="see-also"></a>Ayrıca Bkz.
 [C# Derleyici - delaysign seçeneği](delaysign-compiler-option.md)  
 [C# Derleyici - keyfile seçeneği](keyfile-compiler-option.md)  
 [C# Derleyici - keycontainer seçeneği](keycontainer-compiler-option.md)  
 [C# Derleyici Seçenekleri](index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
