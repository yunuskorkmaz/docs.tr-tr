---
title: "Zayıf Başvurular"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a>Zayıf Başvurular
Uygulamanın kodu söz konusu nesne ulaşabilir sırada atık toplayıcı bir uygulama tarafından kullanılan bir nesne toplayamazsınız. Uygulama nesnesi için güçlü bir başvuru barındırıyor olarak sınıflandırılır.  
  
 Zayıf başvuru hala nesneye erişim uygulama verirken nesne toplamak için atık toplayıcı izin verir. Zayıf başvuru yalnızca belirsiz süreyi güçlü başvuru mevcut nesne toplanır kadar sırasında geçerlidir. Zayıf başvuru kullandığınızda, uygulama, toplanmakta olan engelleyen nesne, güçlü bir başvuru elde edebilirsiniz. Bununla birlikte, her zaman güçlü bir başvuru yeniden önce atık toplayıcı nesnesine ilk alırsınız riski yoktur.  
  
 Zayıf başvurular çok miktarda bellek kullanır, ancak atık toplama tarafından kazanılır varsa kolaylıkla yeniden oluşturulabilir nesneler için faydalıdır.  
  
 Bir Windows Forms uygulaması ağaç görünümünde seçenekleri karmaşık hiyerarşik seçimine kullanıcıya görüntüler varsayalım. Temel alınan veri büyükse, kullanıcı uygulamada başka bir şey ile söz konusu olduğunda ağaç bellekte tutma yetersiz olduğunu.  
  
 Kullanıcı başka bir uygulamanın parçası için hemen geçiş yaparken kullanabileceğiniz <xref:System.WeakReference> ağaç zayıf başvuru oluşturun ve tüm güçlü başvuruları yok etmek için sınıf. Kullanıcı geri ağacına geçirildiğinde, uygulamanın ağaç güçlü bir başvuru almaya çalıştığında ve, başarılı olursa, ağaç yeniden oluşturuluyor önler.  
  
 Bir nesne zayıf bir başvuru oluşturmanız için oluşturduğunuz bir <xref:System.WeakReference> izlenmesi gereken nesne örneğini kullanarak. Ardından <xref:System.WeakReference.Target%2A> bu nesne ve özgün nesne başvurusu kümesi özelliğine `null`. Kod örneği için bkz: <xref:System.WeakReference> Sınıf Kitaplığı'nda.  
  
## <a name="short-and-long-weak-references"></a>Kısa ve uzun zayıf başvurular  
 Bir kısa zayıf bir başvuru veya uzun zayıf oluşturabilirsiniz:  
  
-   kısa  
  
     Başvuru hedef için bir kısa zayıf hale `null` zaman nesne iadesi atık toplama tarafından. Zayıf başvuru kendisi yönetilen bir nesne değildir ve herhangi bir yönetilen nesne gibi çöp toplama tabidir.  Kısa zayıf için varsayılan oluşturucu başvurudur <xref:System.WeakReference>.  
  
-   uzun  
  
     Uzun zayıf başvurusu nesnenin sonra tutulur <xref:System.Object.Finalize%2A> yöntemi çağrılır. Bu nesnenin yeniden oluşturulması için sağlar, ancak nesnenin durumunu öngörülemeyen kalır. Uzun bir referans kullanmak üzere belirtmek `true` içinde <xref:System.WeakReference> Oluşturucusu.  
  
     Nesnenin türü yoksa bir <xref:System.Object.Finalize%2A> yöntemi, kısa zayıf başvuru işlevselliği uygular ve hedef toplanan kadar herhangi bir zaman sonra sonlandırıcıyı oluşabilen çalıştırılan yalnızca zayıf başvurusu geçerli değil.  
  
 Güçlü bir başvuru kurmak ve nesne yeniden kullanmak için cast <xref:System.WeakReference.Target%2A> özelliği bir <xref:System.WeakReference> türde bir nesne. Varsa <xref:System.WeakReference.Target%2A> özelliği döndürür `null`nesne toplanan; Aksi takdirde, uygulamanın yeniden elde, güçlü bir başvuru olduğundan nesne kullanmaya devam edebilirsiniz.  
  
## <a name="guidelines-for-using-weak-references"></a>Zayıf başvurular kullanma için yönergeler  
 Uzun zayıf başvurular yalnızca gerekli olduğunda nesnenin durumunu sonlandırma sonra öngörülemeyen olduğu gibi kullanın.  
  
 İşaretçi olarak büyük veya daha büyük olabilir çünkü küçük nesnelere zayıf başvurular kullanmaktan kaçının.  
  
 Bellek yönetimi sorunları için otomatik bir çözüm olarak zayıf başvurular kullanmaktan kaçının. Bunun yerine, uygulamanızın nesneleri işlemek için etkili bir önbellek İlkesi geliştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çöp toplama](../../../docs/standard/garbage-collection/index.md)
