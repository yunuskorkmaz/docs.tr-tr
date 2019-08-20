---
title: -subsystemversion (C# derleyici seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: c3d056458e1b98e6111216e20620117a9882ad4e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602517"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (C# derleyici seçenekleri)

Oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt sistemin en düşük sürümünü belirtir ve bu sayede yürütülebilir dosyanın çalışacağı Windows sürümlerini belirler. En yaygın olarak, bu seçenek yürütülebilir dosyanın eski Windows sürümleriyle kullanılamayan belirli güvenlik özelliklerinden yararlanmasını sağlar.

> [!NOTE]
>  Alt sistemin kendisini belirtmek için [-target](./target-compiler-option.md) derleyici seçeneğini kullanın.

## <a name="syntax"></a>Sözdizimi

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametreler

`major.minor`

Alt sistemin gerekli en düşük sürümü, birincil ve ikincil sürümler için nokta gösteriminde ifade edilir. Örneğin, bu seçeneğin değerini 6,01 olarak ayarlarsanız, uygulamanın bu konunun ilerleyen kısımlarında açıklandığı gibi, bir uygulamanın Windows 7 ' den eski bir işletim sisteminde çalışabilebileceğinizi belirtebilirsiniz. `major` Ve`minor` değerlerini tamsayılar olarak belirtmeniz gerekir.

`minor` Sürümdeki öndeki sıfırlar sürümü değiştirmez, ancak sonunda sıfır yapılır. Örneğin, 6,1 ve 6,01 aynı sürüme başvurun, ancak 6,10 farklı bir sürüme başvurur. Karışıklığın önüne geçmek için küçük sürümü iki basamakla ifade etmenizi öneririz.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tabloda, Windows 'un ortak alt sistem sürümleri listelenmektedir.

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

**-Subsystemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listede yer alan koşullara bağlıdır:

- Aşağıdaki listede herhangi bir derleyici seçeneğinin ayarlanmış olması halinde varsayılan değer 6,02 ' dir:

  - [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [-target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-platform:arm](./platform-compiler-option.md)

- MSBuild kullanıyorsanız varsayılan değer 6,00 ' dir. .NET Framework 4,5 ' i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini belirlemediniz.

- Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00 ' dir.

## <a name="setting-this-option"></a>Bu seçeneği ayarlama

Visual Studio 'da **-subsystemversion** derleyici seçeneğini ayarlamak için,. csproj dosyasını açmanız ve MSBuild xml içindeki `SubsystemVersion` özelliği için bir değer belirtmeniz gerekir. Visual Studio IDE 'de bu seçeneği ayarlayamazsınız. Daha fazla bilgi için bu konunun önceki kısımlarında "varsayılan değerler" veya [genel MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
