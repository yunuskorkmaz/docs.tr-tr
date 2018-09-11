---
title: Üye aşırı yüklemesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273235"
---
# <a name="member-overloading"></a>Üye aşırı yüklemesi
Üye aşırı yüklemesi, iki veya daha fazla üye, yalnızca sayı veya parametre türünü farklılık gösterir ancak aynı ada sahip aynı türde oluşturma anlamına gelir. Örneğin, aşağıdaki içinde `WriteLine` yöntemi aşırı yüklüdür:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Yalnızca yöntemler, Oluşturucular ve Dizinli Özellikler parametreleri olabileceğinden, yalnızca bu üyeleri aşırı yüklenebilir.  
  
 Aşırı yükleme, kullanılabilirlik, üretkenlik ve yeniden kullanılabilir kitaplıklar okunabilirliğini geliştirmek için en önemli teknikleri biridir. Parametre sayısına göre aşırı yüklemesi, daha basit sürümlerini Kurucular ve yöntemler sağlamak mümkün kılar. Parametre türü üzerinde aşırı yükleme üyelerinin farklı türleri seçili kümesi aynı işlemleri gerçekleştirmek için aynı üye adını kullanmayı mümkün kılar.  
  
 **✓ DO** kısa aşırı yüklemeler tarafından kullanılan varsayılan belirtmek için açıklayıcı parametre adları kullanmayı deneyin.  
  
 **X AVOID** rasgele aşırı parametre adlarında değişen. Başka bir aşırı parametre olarak aynı girişe bir aşırı parametre temsil ediyorsa, parametreleri aynı ada sahip.  
  
 **X AVOID** parametrelerinde sıralama içinde tutarsız olan aşırı yüklenmiş üyeler. Aynı adlı parametreleri, tüm aşırı yüklemeler aynı konumda görüntülenmelidir.  
  
 **✓ DO** (genişletilebilirlik gerekliyse) yalnızca en uzun aşırı sanal olun. Kısa aşırı yüklemeleri yalnızca aracılığıyla için uzun bir aşırı yüklemesini çağırmalıdır.  
  
 **X DO NOT** kullanmak `ref` veya `out` üyeleri aşırı yüklemeyi değiştiricileri.  
  
 Bazı diller, benzer aşırı yüküne çağrıları çözümlenemiyor. Ayrıca, stl'yi Bu aşırı genellikle tamamen farklı semantiklere sahip ve büyük olasılıkla aşırı ancak iki ayrı yöntem bunun yerine olmamalıdır.  
  
 **X DO NOT** aşırı aynı konuma ve benzer türleri parametrelerle henüz farklı semantiği ile sahip.  
  
 **✓ DO** izin `null` isteğe bağlı bağımsız değişkenler için geçirilecek.  
  
 **✓ DO** varsayılan bağımsız değişkenler üyeleriyle tanımlama yerine aşırı üye kullanın.  
  
 Varsayılan bağımsız değişkenler, CLS uyumlu değil.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
