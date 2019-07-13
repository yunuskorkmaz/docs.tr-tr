---
ms.openlocfilehash: 08c16f261338148619de2e484c73046b9d9a6bfe
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858395"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 4.5.x.x sürüm kendisini kayıt defterinde kaydederken kullanmaz

|   |   |
|---|---|
|Ayrıntılar|Sürüm anahtarı bir bekleyebileceğiniz gibi kayıt defterinde ayarlayın (adresindeki <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) için .NET Framework 4. 6 '4.6 ile', '4.5' değil başlar. Hangi .NET Framework sürümlerinin bir makinede yüklü olduğunu öğrenmek için bu kayıt defteri anahtarlarını bağımlı uygulamalar, 4.6 mümkün olan yeni bir sürüm olduğunu ve önceki 4.5.x ile uyumlu olan bir serbest anlamak için güncelleştirilmesi gerekir.|
|Öneri|.NET Framework 4.5 için yoklama uygulamaları güncelleştir 4.5 kayıt defteri anahtarlarını da 4.6 kabul edecek şekilde bakarak yükleyin.|
|`Scope`|Kenar|
|Version|4.6|
|Type|Çalışma zamanı|

