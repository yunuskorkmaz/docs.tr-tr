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
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970439"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# Derleyici Seçenekleri)

Bu seçenek, derleyicinin çıktı dosyasında yer ayırmasına neden olur, böylece dijital imza daha sonra eklenebilir.

## <a name="syntax"></a>Sözdizimi

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`+`&#124;`-`

Tam imzalı bir montaj istiyorsanız **-delaysign-** kullanın. Ortak anahtarı yalnızca derlemeye yerleştirmek istiyorsanız **-delaysign+** kullanın. Varsayılan **-delaysign-**.

## <a name="remarks"></a>Açıklamalar

**-delaysign** seçeneği [-keyfile](./keyfile-compiler-option.md) veya [-keycontainer](./keycontainer-compiler-option.md)ile kullanılmadığı sürece hiçbir etkisi yoktur.

**-delaysign** **ve-publicsign** seçenekleri birbirini dışlar.

Tam olarak imzalanmış bir derleme istediğinizde, derleyici, manifesto (derleme meta verileri) içeren dosyayı ve özel anahtarla karma işaretleri içeren dosyayı haşlar. Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur. Bir derleme geciktiğinde, derleyici imzayı hesaplamaz ve depolamaz, ancak imzanın daha sonra eklenabilmesi için dosyada yer ayırır.

Örneğin, **-delaysign+** kullanmak, bir testedenin derlemeyi genel önbelleğe koymasına olanak tanır. Test ten sonra, [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tam olarak imzalayabilirsiniz.

Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md) [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikleri** sayfasını açın.
1. Yalnızca **Gecikme işareti** özelliğini değiştirin.

Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [C# -publicsign seçeneği](publicsign-compiler-option.md)
- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
