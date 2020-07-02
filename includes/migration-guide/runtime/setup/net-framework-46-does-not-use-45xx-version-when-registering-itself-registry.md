---
ms.openlocfilehash: 09fb7a54fccd5cf37800483c64e2fa6a54681f11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621430"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4,6, kayıt defterine kendisini kaydederken 4.5. x. x sürümünü kullanmaz

#### <a name="details"></a>Ayrıntılar

Bir tane beklendiğinde, 4,6 .NET Framework için kayıt defterindeki (at) kayıt defteri 'nde ayarlanan sürüm anahtarı ' <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> 4,6 ' ile başlar, ' 4,5 ' değil. Bir makineye hangi .NET Framework sürümlerinin yüklendiğini öğrenmek için bu kayıt defteri anahtarlarına bağımlı olan uygulamalar, 4,6 'in yeni bir olası sürüm olduğunu ve bir önceki 4.5. x sürümleriyle uyumlu olduğunu anlamak için güncelleştirilmeleri gerekir.

#### <a name="suggestion"></a>Öneri

4,5 kayıt defteri anahtarlarını arayarak 4,6 de kabul etmek için .NET Framework 4,5 yüklemesi için uygulamaları yoklayan güncelleştirme.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
