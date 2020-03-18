---
title: -publicsign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662536"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (C# Derleyici Seçenekleri)

Bu seçenek derleyicinin ortak bir anahtar uygulamasına neden olur, ancak derlemeyi gerçekte imzalamaz. **-publicsign** seçeneği de dosyanın gerçekte imzalanmış olduğunu çalışma zamanı söyler derleme biraz ayarlar.

## <a name="syntax"></a>Sözdizimi

```console
-publicsign
```

## <a name="arguments"></a>Bağımsız Değişkenler

Yok.

## <a name="remarks"></a>Açıklamalar

**-publicsign** seçeneği [-keyfile](keyfile-compiler-option.md) veya [-keycontainer](keycontainer-compiler-option.md)kullanımını gerektirir. **Anahtar dosyası** veya **anahtar kapsayıcı** seçenekleri ortak anahtarı belirtir.

**-publicsign** **ve-delaysign** seçenekleri birbirini dışlar.

Bazen "sahte işaret" veya "OSS işareti" olarak adlandırılan, genel imza bir çıktı derlemesinde ortak anahtarı içerir ve "imzalı" bayrağı ayarlar, ancak aslında özel bir anahtarla derlemeyi imzalamaz. Bu, insanların yayımlanan "tam olarak imzalanmış" derlemelerle uyumlu derlemeler oluşturmak istedikleri, ancak derlemeleri imzalamak için kullanılan özel anahtara erişemedikleri açık kaynak projeleri için yararlıdır. Hemen hemen hiç tüketici aslında montaj tam olarak imzalanmış olup olmadığını kontrol etmek gerekir, bu kamuya inşa meclisleri tam olarak imzalanmış bir kullanılacak hemen hemen her senaryoda kullanılabilir.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikleri** sayfasını açın.
1. Yalnızca **Gecikme işareti** özelliğini değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici -delaysign işareti seçeneği](delaysign-compiler-option.md)
- [C# Derleyici -keyfile seçeneği](keyfile-compiler-option.md)
- [C# Derleyici -keycontainer seçeneği](keycontainer-compiler-option.md)
- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
