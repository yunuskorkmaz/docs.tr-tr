---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858395"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6, kayıt defterine kayıt yaptırırken 4.5.x.x sürümü kullanmaz

|   |   |
|---|---|
|Ayrıntılar|Tahmin edebileceğiniz gibi, .NET Framework 4.6 <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>için kayıt defterinde (at) ayarlanan sürüm anahtarı '4.5' ile değil ,4.6 ile başlar. Bir makineye hangi .NET Framework sürümlerinin yüklendiğine dair bu kayıt defteri anahtarlarına bağlı olan uygulamalar, 4.6'nın yeni bir olası sürüm olduğunu ve önceki 4.5.x sürümleriyle uyumlu olduğunu anlamak için güncelleştirilmelidir.|
|Öneri|4.6'yı da kabul etmek için 4.5 kayıt defteri anahtarlarını arayarak .NET Framework 4.5 yüklemesi için sondalama uygulamalarını güncelleştirin.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
