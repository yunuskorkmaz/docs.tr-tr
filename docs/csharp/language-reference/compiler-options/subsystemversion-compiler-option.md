---
title: -subsystemversion (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: 25391dd504fb8a2b9458fd9495477258fc23d81a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215520"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (C# Derleyici Seçenekleri)
Böylece yürütülebilir dosyayı çalıştırmak Windows sürümlerinin belirleme oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt en düşük sürümünü belirtir. En yaygın olarak, bu seçeneği, yürütülebilir dosyanın daha eski Windows sürümlerinde kullanılamaz belirli güvenlik özellikleri yararlanabilirsiniz sağlar.  
  
> [!NOTE]
>  Alt belirtmek için kullanın [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parametreler  
 `major.minor`  
 Alt sistemi sürümü, birincil ve ikincil sürümleri için noktalı gösterim ifade gibi gerekli olan en düşük. Örneğin, bir uygulama 6.01 için bu seçeneği değerini ayarlarsanız, bu konunun ilerleyen bölümlerinde tabloda açıklandığı gibi Windows 7'den daha eski bir işletim sisteminde çalışamaz belirtebilirsiniz. Değerleri belirtmelisiniz `major` ve `minor` tamsayı olarak.  
  
 Önde gelen sıfır `minor` sürüm sürümü değişmez, ancak bunu sondaki sıfırlar. Örneğin, aynı sürüm 6.1 ve 6.01 bakın, ancak farklı bir sürüme 6.10 başvuruyor. Karışıklığı önlemek için iki basamaklı olarak alt sürüm ifade öneririz.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda Windows ortak alt sistemi sürümleri listelenmiştir.  
  
|Windows sürümü|Alt sistemi sürümü|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>Varsayılan değerler  
 Varsayılan değer olan **- subsystemversion** derleyici seçeneği, aşağıdaki listeden koşulların bağlıdır:  
  
-   Aşağıdaki listede herhangi bir derleyici seçeneği ayarlandıysa varsayılan değeri 6.02 şöyledir:  
  
    -   [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [-platform:arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   MSBuild kullanıyorsanız, varsayılan değer 6,00, hedefleme [!INCLUDE[net_v45](~/includes/net-v45-md.md)], ve bu listede daha önce belirtilmiş derleyici seçenekleri hiçbirini ayarlamadıysanız.  
  
-   Önceki koşulların hiçbiri true ise varsayılan değer 4.00 ' dir.  
  
## <a name="setting-this-option"></a>Bu seçeneği ayarlama  
 Ayarlamak için **- subsystemversion** derleyici seçeneği Visual Studio'da .csproj dosyasını açın ve için bir değer belirtmeniz gerekir `SubsystemVersion` MSBuild XML özellik. Bu seçenek, Visual Studio IDE içinde ayarlanamıyor. Daha fazla bilgi için bu konunun önceki kısımlarında "Varsayılan değerler" konusuna bakın veya [yaygın MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
