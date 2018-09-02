---
title: -publicsign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 01ce30b9ac5997f56f29dcbbfa43a27738fa5556
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474258"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (C# Derleyici Seçenekleri)

Bu seçenek, bir ortak anahtar uygulamak derleyicinin ancak aslında derlemeyi imzalamayı değil. **- Publicsign** seçeneği de ayarlar biraz derlemesinde çalışma zamanı dosyanın gerçekten imzalı olduğunu belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-publicsign
```

## <a name="arguments"></a>Arguments

Yok.

## <a name="remarks"></a>Açıklamalar

**- Publicsign** seçeneği kullanılmasını gerektiren [- keyfile](keyfile-compiler-option.md) veya [- keycontaıner](keycontainer-compiler-option.md). **Keyfile** veya **keycontainer** seçeneklerini ortak anahtarı belirtin.

**- Publicsign** ve **- delaysıgn** seçenekleri karşılıklı olarak birbirini dışlar.

"Sahte işareti" veya "OSS işareti" olarak da adlandırılır, ortak imzalama çıkış bir derlemede ortak anahtarı içerir ve "imzalı" bayrağını ayarlar, ancak derlemeyi özel anahtarla gerçekten imzalamak değil. Bu kişiler yayımlanan "tam olarak imzalı" derlemeleri ile uyumludur, ancak derlemeleri imzalamak için kullanılan özel anahtar erişimi olmayan derlemeler oluşturmak istediğiniz açık kaynak projeleri için kullanışlıdır. Neredeyse hiçbir tüketiciler derleme tam olarak imzalı denetlemek gerçekten gerekli olduğundan, bunlar genel olarak derlenen bütünleştirilmiş kodlarda nerede tam olarak imzalı bir kullanılan neredeyse her senaryoda kendisini adamıştır.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Açık **özellikleri** proje sayfası.
1. Değiştirme **gecikme yalnızca oturum** özelliği.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici - delaysıgn seçeneği](delaysign-compiler-option.md)  
- [C# derleyicisi - keyfıle seçeneği](keyfile-compiler-option.md)  
- [C# Derleyici - keycontaıner seçeneği](keycontainer-compiler-option.md)  
- [C# Derleyici Seçenekleri](index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
