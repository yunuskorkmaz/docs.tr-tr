---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 09ddc4bb735b645e09d34198c66dff78183592bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403089"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt sistemin en düşük sürümünü belirtir ve bu sayede yürütülebilir dosyanın çalışacağı Windows sürümlerini belirler. En yaygın olarak, bu seçenek yürütülebilir dosyanın eski Windows sürümleriyle kullanılamayan belirli güvenlik özelliklerinden yararlanmasını sağlar.

> [!NOTE]
> Alt sistemin kendisini belirtmek için [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneğini kullanın.

## <a name="syntax"></a>Söz dizimi

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametreler

`major.minor`

Alt sistemin gerekli en düşük sürümü, birincil ve ikincil sürümler için nokta gösteriminde ifade edilir. Örneğin, bu seçeneğin değerini 6,01 olarak ayarlarsanız, uygulamanın bu konunun ilerleyen kısımlarında açıklandığı gibi, bir uygulamanın Windows 7 ' den eski bir işletim sisteminde çalışabilebileceğinizi belirtebilirsiniz. Ve değerlerini tamsayılar olarak belirtmeniz gerekir `major` `minor` .

Sürümdeki öndeki sıfırlar `minor` sürümü değiştirmez, ancak sonunda sıfır yapılır. Örneğin, 6,1 ve 6,01 aynı sürüme başvurun, ancak 6,10 farklı bir sürüme başvurur. Karışıklığın önüne geçmek için küçük sürümü iki basamakla ifade etmenizi öneririz.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tabloda, Windows 'un ortak alt sistem sürümleri listelenmektedir.

|Windows sürümü|Alt sistem sürümü|
|---------------------|-----------------------|
|Windows 2000|5,00|
|Windows XP|5,01|
|Windows Server 2003|5,02|
|Windows Vista|6,00|
|Windows 7|6,01|
|Windows Server 2008|6,01|
|Windows 8|6,02|

## <a name="default-values"></a>Varsayılan değerler

**-Subsystemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listede yer alan koşullara bağlıdır:

- Aşağıdaki listede herhangi bir derleyici seçeneğinin ayarlanmış olması halinde varsayılan değer 6,02 ' dir:

  - [-target:appcontainerexe](target.md)

  - [-target:winmdobj](target.md)

  - [-Platform: ARM](platform.md)

- MSBuild kullanıyorsanız varsayılan değer 6,00 ' dir. .NET Framework 4,5 ' i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini belirlemediniz.

- Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00 ' dir.

## <a name="setting-this-option"></a>Bu seçeneği ayarlama

Visual Studio 'da **-subsystemversion** derleyici seçeneğini ayarlamak için,. vbproj dosyasını açmanız ve `SubsystemVersion` MSBuild xml içindeki özelliği için bir değer belirtmeniz gerekir. Visual Studio IDE 'de bu seçeneği ayarlayamazsınız. Daha fazla bilgi için bu konunun önceki kısımlarında "varsayılan değerler" veya [genel MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)

- [MSBuild Özellikleri](/visualstudio/msbuild/msbuild-properties)
