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
ms.openlocfilehash: 2c77f08cd573dc40083718b783ae01233ca00766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573561"
---
# <a name="member-overloading"></a>Üye aşırı yüklemesi
Üye aşırı yüklemesi, iki veya daha fazla üye, yalnızca sayısını veya parametre türünü farklılık gösterir ancak aynı ada sahip aynı türde oluşturmak anlamına gelir. Örneğin, aşağıdakileri de `WriteLine` yöntemi aşırı yüklenmiş:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Yalnızca yöntemleri oluşturucular ve Dizinli Özellikler parametreleri olabileceğinden, bu üyeler yalnızca aşırı yüklenmiş.  
  
 Aşırı yüklemesi, kullanılabilirlik, verimliliği ve yeniden kullanılabilir kitaplıkları okunabilirliğini artırmak için en önemli teknikler biridir. Parametrelerin sayısı aşırı oluşturucular ve yöntemleri daha basit sürümlerini sağlamak mümkün kılar. Parametre türü aşırı yüklemesi farklı türleri seçili kümesi üzerinde aynı işlemler üyeleri için aynı üye adı kullanmayı mümkün kılar.  
  
 **✓ DO** kısa aşırı yüklemeler tarafından kullanılan varsayılan belirtmek için açıklayıcı parametre adları kullanmayı deneyin.  
  
 **X AVOID** rasgele aşırı parametre adlarında değişen. Aynı giriş başka bir aşırı içindeki bir parametre olarak bir aşırı parametresinde temsil ediyorsa parametreleri aynı ada sahip.  
  
 **X AVOID** parametrelerinde sıralama içinde tutarsız olan aşırı yüklenmiş üyeler. Aynı adlı parametreleri, tüm aşırı aynı konumda görüntülenmelidir.  
  
 **✓ DO** (genişletilebilirlik gerekliyse) yalnızca en uzun aşırı sanal olun. Daha kısa aşırı yalnızca üzerinden uzun bir aşırı yüklemesine çağırmanız gerekir.  
  
 **X DO NOT** kullanmak `ref` veya `out` üyeleri aşırı yüklemeyi değiştiricileri.  
  
 Bazı diller şöyle aşırı çağrıları çözümlenemiyor. Ayrıca, bu tür aşırı genellikle tamamen farklı semantiklerine sahip ve büyük olasılıkla aşırı ancak iki ayrı yöntem bunun yerine olmamalıdır.  
  
 **X DO NOT** aşırı aynı konuma ve benzer türleri parametrelerle henüz farklı semantiği ile sahip.  
  
 **✓ DO** izin `null` isteğe bağlı bağımsız değişkenler için geçirilecek.  
  
 **✓ DO** varsayılan bağımsız değişkenler üyeleriyle tanımlama yerine aşırı üye kullanın.  
  
 Varsayılan bağımsız değişkenler, CLS uyumlu değildir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
