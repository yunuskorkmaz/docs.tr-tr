---
description: 'Daha fazla bilgi edinin: üye aşırı yüklemesi'
title: Üye Aşırı Yüklemesi
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: d3a545bfec552686e55c9f713d58784497946819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641960"
---
# <a name="member-overloading"></a>Üye Aşırı Yüklemesi

Üye aşırı yüklemesi, aynı türde yalnızca parametre sayısı veya türünde farklı ancak aynı ada sahip iki veya daha fazla üye oluşturma anlamına gelir. Örneğin, aşağıdaki, `WriteLine` yöntemi aşırı yüklenmiştir:

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 Yalnızca Yöntemler, oluşturucular ve dizinli Özellikler parametrelere sahip olabileceğinden yalnızca bu Üyeler aşırı yüklenebilir.

 Aşırı yükleme, yeniden kullanılabilir kitaplıkların kullanılabilirliğini, verimliliğini ve okunabilirliğini iyileştirmeye yönelik en önemli tekniklerden biridir. Parametrelerin sayısı üzerinde aşırı yükleme, oluşturucuların ve yöntemlerin daha basit sürümlerini sağlamayı olanaklı kılar. Parametre türü üzerinde aşırı yükleme, seçilen farklı türde bir küme üzerinde özdeş işlemler gerçekleştiren Üyeler için aynı üye adını kullanmayı mümkün kılar.

 ✔️ daha kısa aşırı yüklemeler tarafından kullanılan varsayılan adı belirtmek için açıklayıcı parametre adları kullanmayı deneyin.

 ❌ Aşırı yüklerde rasgele değişen parametre adlarından KAÇıNıN. Bir aşırı yükteki bir parametre başka bir aşırı yükteki parametre ile aynı girişi gösteriyorsa, parametrelerin aynı ada sahip olması gerekir.

 ❌ Aşırı yüklenmiş Üyeler içindeki parametrelerin sıralaması için tutarsız yapmaktan kaçının. Aynı ada sahip parametreler tüm aşırı yüklerdeki aynı konumda görünmelidir.

 ✔️ yalnızca en uzun aşırı yükleme sanal (genişletilebilirlik gerekliyse) yapın. Daha kısa aşırı yüklemeler yalnızca daha uzun bir aşırı yüklemeye çağrı yapmanız gerekir.

 ❌`ref` `out` Üyeleri aşırı yüklemek için veya değiştiricilerini kullanmayın.

 Bazı diller bunun gibi aşırı yüklemelerin çağrılarını çözemez. Buna ek olarak, bu aşırı yüklemeler genellikle tamamen farklı semantiklere sahiptir ve muhtemelen aşırı yükleme olmaması gerekir, bunun yerine iki ayrı Yöntem

 ❌ Aynı konumda ve benzer türlerde parametrelere sahip tekrar yüklemeler yoktur, ancak bu farklı semantiklerdir.

 `null`isteğe bağlı bağımsız değişkenler için ✔️ izin verme.

 ✔️ Varsayılan bağımsız değişkenlerle üyeleri tanımlamak yerine üye aşırı yüklemeyi kullanın.

 Varsayılan bağımsız değişkenler CLS uyumlu değildir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
