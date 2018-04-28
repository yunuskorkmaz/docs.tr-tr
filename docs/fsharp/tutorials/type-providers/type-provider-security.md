---
title: Tür Sağlayıcısı Güvenliği
description: 'F tür sağlayıcısı güven ayarlarını değiştirmek nasıl dahil olmak üzere #, tür sağlayıcısı güvenliği hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4f0b55062aec6c560112fe10ca4df77f42493011
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="type-provider-security"></a>Tür Sağlayıcısı Güvenliği

Türü, dış veri kaynaklarına bağlanmak ve bu tür bilgiler F # türü ortamına yüzey için kod içeren F # proje veya komut dosyası tarafından başvurulan derlemeler (dll) sağlayıcılarıdır. Genellikle, derleyin ve ardından kod yürütmek (veya bir komut dosyası söz konusu olduğunda kodu F # Etkileşimli'ye gönderdiğinizde) başvurulan derlemelerin kodda yalnızca çalıştırılır. Bununla birlikte, Kod düzenleyicisinde yalnızca gözatarken türü sağlayıcı derlemesi Visual Studio içinde çalışır. Tür sağlayıcıları hızlı bilgi araç ipuçlarını, IntelliSense tamamlamalar gibi Düzenleyicisi ek bilgi eklemek üzere çalıştırmanız gerekir çünkü bu gerçekleşir. Sonuç olarak, ek güvenlik noktalar vardır türü için sağlayıcı derlemeleri, Visual Studio işlemi içinde otomatik olarak çalıştırdıkları beri.


## <a name="security-warning-dialog"></a>Güvenlik Uyarısı iletişim kutusu
Bir türdeki sağlayıcı derlemesi ilk kez kullanırken, Visual Studio, tür sağlayıcısı çalışmak üzere olduğunu sizi uyarır güvenlik iletişim kutusu görüntüler. Visual Studio türü sağlayıcısı yüklemeden önce bu belirli sağlayıcı güveniyorsanız karar verme olanağı sağlar. Tür sağlayıcısı kaynağına güveniyorsanız, ardından "Bu tür sağlayıcısı güvendiğim." seçin Tür sağlayıcısı kaynağına güvenmiyorsanız, ardından "Bu tür sağlayıcısı güvendiğim değil." seçin Sağlayıcı güvenen Visual Studio içinde çalıştırmak ve IntelliSense sağlar ve özellikleri oluşturmak için etkinleştirir. Ancak, tür sağlayıcısı kötü amaçlı ise, kendi kod çalıştıran makinenizi güvenliğinin aşılmasına neden olabilir.

Projenizi güvenmediğiniz için iletişim kutusunda seçtiğiniz tür sağlayıcıları başvuran kodu içeriyorsa, derleme zamanında derleyici tür sağlayıcısı güvenilmeyen olduğunu belirten bir hata bildirir. Güvenilmeyen türü sağlayıcısında bağımlı türleri kırmızı dalgalı çizgiler tarafından belirtilir. Kod Düzenleyicisi'nde göz atmak güvenlidir.

Visual Studio'da doğrudan güven ayarını değiştirmeye karar verirseniz, aşağıdaki adımları gerçekleştirin.


#### <a name="to-change-the-trust-settings-for-type-providers"></a>Tür sağlayıcıları güven ayarlarını değiştirmek için

1. Üzerinde `Tools` menüsünde, select `Options`ve genişletin `F# Tools` düğümü.
<br />

2. Seçin `Type Providers`, tür sağlayıcıları listesinde güvendiğiniz tür sağlayıcıları için onay kutusunu işaretleyin ve güvenmediğiniz olanlar için onay kutusunu temizleyin.
<br />


## <a name="see-also"></a>Ayrıca Bkz.
[Tür Sağlayıcıları](index.md)
