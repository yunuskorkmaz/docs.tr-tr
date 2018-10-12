---
title: Zayıf Başvurular
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65492beb888da1986f456d3fd000fc02f340f3c4
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121109"
---
# <a name="weak-references"></a>Zayıf Başvurular
Uygulamanın kodu söz konusu nesne ulaşabileceği sırada Çöp toplayıcı bir uygulama tarafından kullanılan bir nesne toplayamazsınız. Uygulama, güçlü bir başvuru nesnesine sahip bildirilir.  
  
 Zayıf bir başvuru, çöp toplayıcı nesneyi nesneye erişmek için uygulamayı hala izin verirken toplamak için izin verir. Zayıf bir başvuru yalnızca belirsiz süreyi güçlü başvuru varken nesne toplanana kadar sırasında büyük/küçük harf geçerlidir. Zayıf bir başvuru kullandığınızda, uygulama toplanmasını önleyen nesne, güçlü bir başvuru elde edebilirsiniz. Ancak, her zaman bir güçlü başvuruya kurulmaz önce çöp toplayıcı nesnenin ilk alırsınız riski yoktur.  
  
 Zayıf başvurular, çok miktarda bellek kullanır, ancak çöp toplama tarafından talep edilen, kolayca yeniden oluşturulabilir nesneler için kullanışlıdır.  
  
 Bir Windows Forms uygulaması ağaç görünümünde, kullanıcıya bir karmaşık hiyerarşik, tercih ettiğiniz seçenekleri görüntüler varsayalım. Temel alınan veriler büyükse, ağaç bellekte tutulması, kullanıcı uygulamada başka bir şey ile söz konusu olduğunda verimsizdir.  
  
 Kullanıcı başka bir uygulamanın parçası için hemen geçtiğinde kullanabileceğiniz <xref:System.WeakReference> zayıf bir başvuru ağacı oluşturmak ve tüm güçlü atıflar yok etmek için sınıf. Kullanıcı ağaca geri dön geçirildiğinde, uygulamanın güçlü bir başvuru ağacı almayı dener ve, başarılı olursa, ağaç yeniden oluşturuluyor önler.  
  
 Zayıf bir başvuru içeren bir nesne oluşturmak için oluşturduğunuz bir <xref:System.WeakReference> izlenmesi nesnesinin örneğini kullanarak. Ardından <xref:System.WeakReference.Target%2A> bu nesne ve özgün nesneye başvurusu kümesi özelliğini `null`. Kod örneği için bkz: <xref:System.WeakReference> Sınıf Kitaplığı'nda.  
  
## <a name="short-and-long-weak-references"></a>Kısa ve uzun zayıf başvurular  
 Zayıf bir başvuru kısa veya uzun zayıf bir başvuru oluşturabilirsiniz:  
  
-   kısa  
  
     Kısa bir zayıf başvuru hedefinin olur `null` zaman nesne iadesi çöp toplama tarafından. Zayıf başvuru kendisi yönetilen bir nesnedir ve çöp toplama gibi herhangi bir yönetilen nesne tabidir.  Kısa bir zayıf başvuru olduğu için varsayılan oluşturucu <xref:System.WeakReference>.  
  
-   uzun  
  
     Nesnenin sonra uzun zayıf bir başvuru korunur <xref:System.Object.Finalize%2A> yöntemi çağrılır. Bu nesnenin oluşturulması sağlar, ancak nesnenin durumu beklenmedik kalır. Uzun bir başvuru kullanılacağını belirtin `true` içinde <xref:System.WeakReference> Oluşturucusu.  
  
     Nesnenin türü yoksa bir <xref:System.Object.Finalize%2A> yöntemi, kısa zayıf başvuru işlevselliğini uygular ve hedef toplanana kadar sonra dilediğiniz zaman Sonlandırıcı oluşabilen çalıştırılan yalnızca zayıf başvuru geçerli değil.  
  
 Güçlü bir başvuru'kurmak ve nesne yeniden kullanmak için tür dönüştürme <xref:System.WeakReference.Target%2A> özelliği bir <xref:System.WeakReference> nesnenin türü. Varsa <xref:System.WeakReference.Target%2A> özelliği döndürür `null`nesne toplanan; Aksi takdirde, uygulamanın kendisine güçlü başvuru buldum olduğundan, nesne kullanmaya devam edebilirsiniz.  
  
## <a name="guidelines-for-using-weak-references"></a>Zayıf başvurular kullanma yönergeleri  
 Yalnızca gerekli olduğunda nesnenin durumu sonlandırma sonra tahmin edilemez şekilde uzun zayıf başvurular kullanın.  
  
 Zayıf başvurular küçük nesneleri için işaretçi kadar büyük ya da daha büyük olabileceğinden kullanmaktan kaçının.  
  
 Zayıf başvurular bellek yönetimi sorunları için otomatik bir çözüm olarak kullanmaktan kaçının. Bunun yerine, uygulamanızın nesneleri işlemek için geçerli bir önbelleğe alma ilkesinin geliştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
