---
title: Üye Aşırı Yüklemesi
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: 6a2cd6d4dd293a7f4a408e1ee97a125c9454be41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289011"
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

 ❌Aşırı yüklerde rasgele değişen parametre adlarından KAÇıNıN. Bir aşırı yükteki bir parametre başka bir aşırı yükteki parametre ile aynı girişi gösteriyorsa, parametrelerin aynı ada sahip olması gerekir.

 ❌Aşırı yüklenmiş Üyeler içindeki parametrelerin sıralaması için tutarsız yapmaktan kaçının. Aynı ada sahip parametreler tüm aşırı yüklerdeki aynı konumda görünmelidir.

 ✔️ yalnızca en uzun aşırı yükleme sanal (genişletilebilirlik gerekliyse) yapın. Daha kısa aşırı yüklemeler yalnızca daha uzun bir aşırı yüklemeye çağrı yapmanız gerekir.

 ❌`ref` `out` Üyeleri aşırı yüklemek için veya değiştiricilerini kullanmayın.

 Bazı diller bunun gibi aşırı yüklemelerin çağrılarını çözemez. Buna ek olarak, bu aşırı yüklemeler genellikle tamamen farklı semantiklere sahiptir ve muhtemelen aşırı yükleme olmaması gerekir, bunun yerine iki ayrı Yöntem

 ❌Aynı konumda ve benzer türlerde parametrelere sahip tekrar yüklemeler yoktur, ancak bu farklı semantiklerdir.

 `null`isteğe bağlı bağımsız değişkenler için ✔️ izin verme.

 ✔️ Varsayılan bağımsız değişkenlerle üyeleri tanımlamak yerine üye aşırı yüklemeyi kullanın.

 Varsayılan bağımsız değişkenler CLS uyumlu değildir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
