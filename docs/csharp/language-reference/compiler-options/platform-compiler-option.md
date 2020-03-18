---
title: -platform (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70849872"
---
# <a name="-platform-c-compiler-options"></a>-platform (C# Derleyici Seçenekleri)

Derlemeyi Ortak Dil Çalışma Zamanı'nın (CLR) hangi sürümünün çalıştırabileceğini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-platform:string
```

## <a name="parameters"></a>Parametreler

`string` \
anycpu (varsayılan), anycpu32bitpreferred, ARM, x64, x86 veya Itanium.

## <a name="remarks"></a>Açıklamalar

- **anycpu** (varsayılan) herhangi bir platformda çalıştırmak için derlemenizi derler. Uygulamanız mümkün olduğunda 64 bit işlem olarak çalışır ve yalnızca bu mod kullanılabilir olduğunda 32 bit'e geri döner.

- **anycpu32bitpreferred** herhangi bir platformda çalıştırmak için montaj derlemeler. Uygulamanız, hem 64 bit hem de 32 bit uygulamaları destekleyen sistemlerde 32 bit modunda çalışır. Bu seçeneği yalnızca .NET Framework 4.5'i hedefleyen projeler için belirtebilirsiniz.

- **ARM,** Gelişmiş RISC Machine (ARM) işlemcisine sahip bir bilgisayarda çalışacak şekilde derlemenizi derler.

- **ARM64, A64** talimat kümesini destekleyen Gelişmiş RISC Machine (ARM) işlemcisine sahip bir bilgisayarda 64 bit CLR tarafından çalışacak şekilde derlemenizi derler.

- **x64,** AMD64 veya EM64T talimat kümesini destekleyen bir bilgisayarda 64 bit CLR tarafından çalıştırılacak şekilde derlemenizi derler.

- **x86,** 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde montajınızı derler.

- **Itanium, itanium** işlemcili bir bilgisayardaki 64 bit CLR tarafından çalıştırılmak üzere derlemenizi derler.

64 bit Windows işletim sisteminde:

- **-platform:x86** ile derlenen derlemeler WOW64 altında çalışan 32 bit CLR'de yürütülür.

- **-platform:anycpu** ile derlenen bir DLL, yüklendiği işlemle aynı CLR'de yürütülür.

- **-platform:anycpu** 64-bit CLR üzerinde yürütülebilir.

- **-platform:anycpu32bitpreferred** 32-bit CLR üzerinde yürütülmesi ile derlenen yürütülebilir.

**Anycpu32bitpreferred** ayarı yalnızca çalıştırılabilir (. EXE) dosyaları ve .NET Framework 4.5 gerektirir.

Windows 64 bit işletim sisteminde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için [64 bit Uygulamalar'a](../../../framework/64-bit-apps.md)bakın.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikleri** sayfasını açın.

2. Özellik **Oluştur** sayfasını tıklatın.

3. Platform **hedef** özelliğini değiştirin ve .NET Framework 4.5'i hedefleyen projeler için **Tercih 32 bit** onay kutusunu seçin veya temizleyin.

> [!NOTE]
> `-platform`Visual C# Express'te geliştirme ortamında kullanılamaz.

Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>

## <a name="example"></a>Örnek

Aşağıdaki örnekte, uygulamanın 64 bit Windows işletim sisteminde 64 bit CLR tarafından çalıştırılması gerektiğini belirtmek için **-platform** seçeneğinin nasıl kullanılacağı gösterilmektedir.

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
