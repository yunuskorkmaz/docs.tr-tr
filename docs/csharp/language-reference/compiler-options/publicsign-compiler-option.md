---
description: -publicsign (C# derleyici seçenekleri)
title: -publicsign (C# derleyici seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124818"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (C# derleyici seçenekleri)

Bu seçenek derleyicinin ortak anahtar uygulamasına, ancak derlemeyi gerçekten imzalamasına neden olur. **-Publicsign** seçeneği Ayrıca derlemede, dosyanın gerçekten imzalandığını belirten bir bit belirler.

## <a name="syntax"></a>Söz dizimi

```console
-publicsign
```

## <a name="arguments"></a>Bağımsız değişkenler

Yok.

## <a name="remarks"></a>Açıklamalar

**-Publicsign** seçeneği, [-keyfile](keyfile-compiler-option.md) veya [-keycontainer](keycontainer-compiler-option.md)kullanımını gerektirir. **Keyfile** veya **keycontainer** seçenekleri ortak anahtarı belirtir.

**-Publicsign** ve **-delaysign** seçenekleri birbirini dışlıyor.

Bazen "sahte imza" veya "OSS işareti" olarak da adlandırılan ortak imzalama, bir çıktı derlemesinde ortak anahtarı içerir ve "imzalanmış" bayrağını ayarlar, ancak aslında derlemeyi özel bir anahtarla imzalayamıyor. Bu, insanların yayınlanan "tam olarak imzalanmış" derlemeleriyle uyumlu derlemeler oluşturmak istediği, ancak derlemeleri imzalamak için kullanılan özel anahtara erişime sahip olmadığı açık kaynaklı projeler için kullanışlıdır. Neredeyse hiçbir tüketiciye derlemenin tamamen imzalanıp imzalanmadığını kontrol etmek zorunda olduğundan, bu genel olarak oluşturulan derlemeler neredeyse her bir senaryoda, tam olarak imzalanan bir şekilde kullanılabilir.

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a>Bir csproj dosyasında bu derleyici seçeneğini ayarlamak için

Bir proje için. csproj dosyasını açın ve şu öğeyi ekleyin:

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyicisi-delaysign seçeneği](delaysign-compiler-option.md)
- [C# Derleyici-anahtar seçeneği](keyfile-compiler-option.md)
- [C# derleyicisi-keycontainer seçeneği](keycontainer-compiler-option.md)
- [C# derleyici seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
