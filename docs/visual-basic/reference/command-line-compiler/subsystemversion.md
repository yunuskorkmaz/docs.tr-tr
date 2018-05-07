---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22eb8aa1cd86dba4a1a65edf31a3b18df7085a33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)
Böylece yürütülebilir dosyayı çalıştırmak Windows sürümlerinin belirleme oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt en düşük sürümünü belirtir. En yaygın olarak, bu seçeneği, yürütülebilir dosyanın daha eski Windows sürümlerinde kullanılamaz belirli güvenlik özellikleri yararlanabilirsiniz sağlar.  
  
> [!NOTE]
>  Alt belirtmek için kullanın [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
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
  
    -   [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-platform:arm](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   MSBuild kullanıyorsanız, varsayılan değer 6,00, hedefleme [!INCLUDE[net_v45](~/includes/net-v45-md.md)], ve bu listede daha önce belirtilmiş derleyici seçenekleri hiçbirini ayarlamadıysanız.  
  
-   Önceki koşulların hiçbiri true ise varsayılan değer 4.00 ' dir.  
  
## <a name="setting-this-option"></a>Bu seçeneği ayarlama  
 Ayarlamak için **- subsystemversion** derleyici seçeneği Visual Studio'da .vbproj dosyasını açın ve için bir değer belirtmeniz gerekir `SubsystemVersion` MSBuild XML özellik. Bu seçenek, Visual Studio IDE içinde ayarlanamıyor. Daha fazla bilgi için bu konunun önceki kısımlarında "Varsayılan değerler" konusuna bakın veya [yaygın MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).  
  

  
## <a name="see-also"></a>Ayrıca Bkz.  
[Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)

[MSBuild Özellikleri](/visualstudio/msbuild/msbuild-properties)
