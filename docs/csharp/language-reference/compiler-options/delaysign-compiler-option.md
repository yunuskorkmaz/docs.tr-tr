---
title: -delaysign (C# derleyici seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: ae309a8de6c4691f0009e5beb8ac2adc8772805b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603030"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# derleyici seçenekleri)

Bu seçenek derleyicinin çıkış dosyasında alan ayırmasını sağlayarak bir dijital imzanın daha sonra eklenebilmesini sağlar.

## <a name="syntax"></a>Sözdizimi

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`

Tam olarak imzalanan bir derlemeyi istiyorsanız **-delaysign-** kullanın. Yalnızca ortak anahtarı derlemeye yerleştirmek istiyorsanız **-delaysign +** kullanın. Varsayılan değer **-delaysign-** .

## <a name="remarks"></a>Açıklamalar

\- [Keyfile](./keyfile-compiler-option.md) veya [-keycontainer](./keycontainer-compiler-option.md)ile kullanılmamışsa **-delaysign** seçeneğinin hiçbir etkisi yoktur.

**-Delaysign** ve **-publicsign** seçenekleri birbirini dışlıyor.

Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar. Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur. Bir derlemenin gecikmesi gecikmeli kaydolduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imzanın daha sonra eklenebilmesi için dosyada alanı ayırır.

Örneğin, **-delaysign +** kullanılması, bir sınayıcı 'ın derlemeyi genel önbellekte almasına izin verir. Test ettikten sonra, derleme [bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tamamen imzalayabilirsiniz.

Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [bir derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikler** sayfasını açın.
1. **Yalnızca gecikmeli imzala** özelliğini değiştirin.

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>Ayrıca bkz.

- [C#-publicsign seçeneği](publicsign-compiler-option.md)
- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
