---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093635"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey.Encode ve MachineKey.Decode yöntemleri artık kullanılmamaktadır

|   |   |
|---|---|
|Ayrıntılar|Bu yöntemler artık kullanım dışıdır. Bu yöntemleri çağıran kodun derlemesi bir derleyici uyarısı meydana getirir.|
|Öneri|Önerilen alternatifler, <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> ve <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternatif olarak, derleme uyarıları gizlenebilir ya da daha eski bir derleyici kullanılarak önlenebilir. API'leri hala desteklenmektedir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
