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
author: KrzysztofCwalina
ms.openlocfilehash: 4caa0ae78d168b23fd2862153bef0e3960d3ea42
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392950"
---
# <a name="member-overloading"></a>Üye Aşırı Yüklemesi
Üye aşırı yüklemesi, aynı türde yalnızca parametre sayısı veya türünde farklı ancak aynı ada sahip iki veya daha fazla üye oluşturma anlamına gelir. Örneğin, aşağıdaki `WriteLine` yöntemi aşırı yüklenmiştir:  
  
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
  
 **✓ DO** kısa aşırı yüklemeler tarafından kullanılan varsayılan belirtmek için açıklayıcı parametre adları kullanmayı deneyin.  
  
 **X AVOID** rasgele aşırı parametre adlarında değişen. Bir aşırı yükteki bir parametre başka bir aşırı yükteki parametre ile aynı girişi gösteriyorsa, parametrelerin aynı ada sahip olması gerekir.  
  
 **X AVOID** parametrelerinde sıralama içinde tutarsız olan aşırı yüklenmiş üyeler. Aynı ada sahip parametreler tüm aşırı yüklerdeki aynı konumda görünmelidir.  
  
 **✓ DO** (genişletilebilirlik gerekliyse) yalnızca en uzun aşırı sanal olun. Daha kısa aşırı yüklemeler yalnızca daha uzun bir aşırı yüklemeye çağrı yapmanız gerekir.  
  
 **X DO NOT** kullanmak `ref` veya `out` üyeleri aşırı yüklemeyi değiştiricileri.  
  
 Bazı diller bunun gibi aşırı yüklemelerin çağrılarını çözemez. Buna ek olarak, bu aşırı yüklemeler genellikle tamamen farklı semantiklere sahiptir ve muhtemelen aşırı yükleme olmaması gerekir, bunun yerine iki ayrı Yöntem  
  
 **X DO NOT** aşırı aynı konuma ve benzer türleri parametrelerle henüz farklı semantiği ile sahip.  
  
 **✓ DO** izin `null` isteğe bağlı bağımsız değişkenler için geçirilecek.  
  
 **✓ DO** varsayılan bağımsız değişkenler üyeleriyle tanımlama yerine aşırı üye kullanın.  
  
 Varsayılan bağımsız değişkenler CLS uyumlu değildir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 @no__t, [Framework tasarım yönergelerinden Pearson Eğitim, Inc. izni ile 0Reyazdırılmıştır: Microsoft Windows geliştirme serisi 'nin bir parçası olarak, .NET kitaplıkları için 2. sürüm @ no__t-0, Vazysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 ile Addison-Wesley Professional için kurallar, deyimler ve desenler. *  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
