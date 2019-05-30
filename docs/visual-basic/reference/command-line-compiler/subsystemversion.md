---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: e42501a002d808f31dc3d599dc030e96c573a22f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380316"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Böylece Windows yürütülebilir dosyayı çalışabileceği sürümleri belirleme oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt en düşük sürümünü belirtir. En yaygın olarak, bu seçeneği, yürütülebilir dosyanın daha eski Windows sürümleri ile kullanılamayan belirli güvenlik özellikleri yararlanabilir sağlar.

> [!NOTE]
> Alt belirtmek için kullanın [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneği.

## <a name="syntax"></a>Sözdizimi

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametreler

`major.minor`

Alt sistem sürümünü, birincil ve ikincil sürüme bir nokta gösterimi ifade olarak gerekli olan en düşük. Örneğin, bir uygulama için 6.01, bu seçenek değerini ayarlarsanız bu konunun ilerleyen bölümlerindeki bir tabloda açıklandığı gibi Windows 7'den eski bir işletim sisteminde çalıştıramazsınız belirtebilirsiniz. Değerleri belirtmelisiniz `major` ve `minor` tamsayılar olarak.

Baştaki sıfırları `minor` sürümü, sürüm değişmez ancak Sondaki sıfırları yapın. Örneğin, aynı sürüme 6.1 ve 6.01 bakın, ancak farklı bir sürüme 6.10 başvuruyor. Alt sürüm iki basamak Karışıklığı önlemek için ifade öneririz.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tabloda Windows ortak alt sistemi sürümlerini listeler.

|Windows sürümü|Alt sistem sürümü|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|

## <a name="default-values"></a>Varsayılan değerler

Varsayılan değer olan **- subsystemversion** derleyici seçeneği, aşağıdaki listede koşul bağlıdır:

- Aşağıdaki listedeki herhangi bir derleyici seçeneği ayarlanırsa varsayılan değeri 6.02 şöyledir:

  - [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-platform:arm](../../../visual-basic/reference/command-line-compiler/platform.md)

- Varsayılan 6.00 MSBuild kullanıyorsanız, .NET Framework 4.5, hedeflediğiniz ve bu listede daha önce belirtilmiş derleyici seçeneklerinden herhangi birini ayarlamasını yapmadığınızı değerdir.

- Yukarıdaki koşulların hiçbiri doğru olması durumunda varsayılan 4.00 değerdir.

## <a name="setting-this-option"></a>Bu seçeneği ayarlama

Ayarlanacak **- subsystemversion** derleyici seçeneğini Visual Studio'da .vbproj dosyasını açın ve için bir değer belirtmeniz gerekir `SubsystemVersion` MSBuild XML özelliği. Visual Studio IDE'de bu seçeneği ayarlanamaz. Daha fazla bilgi için bu konuda daha önce "Varsayılan değerler" konusuna bakın veya [yaygın MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

- [MSBuild Özellikleri](/visualstudio/msbuild/msbuild-properties)
