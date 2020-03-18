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
ms.openlocfilehash: 120777ca3c26b1634bd2143863547cfa4ea5deac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141336"
---
# <a name="weak-references"></a>Zayıf Başvurular
Çöp toplayıcı, uygulamanın kodu bu nesneye ulaşabiliyorken, uygulama tarafından kullanılan bir nesneyi toplayamaz. Uygulama nesne için güçlü bir referans olduğu söyleniyor.  
  
 Zayıf bir başvuru, başvurunun nesneye erişmesine izin verirken çöp toplayıcısının nesneyi toplamasına izin verir. Zayıf bir başvuru, yalnızca nesne güçlü bir başvuru olmadığında toplanana kadar belirsiz süre boyunca geçerlidir. Zayıf bir başvuru kullandığınızda, uygulama nesneye güçlü bir başvuru almaya devam edebilir ve bu da nesnenin toplanmasını engeller. Ancak, güçlü bir başvuru yeniden kurulmadan önce çöp toplayıcısının nesneye ilk olarak gelme riski her zaman vardır.  
  
 Zayıf başvurular, çok fazla bellek kullanan nesneler için yararlıdır, ancak çöp toplama tarafından geri kazanılırsa kolayca yeniden oluşturulabilir.  
  
 Windows Forms uygulamasındaki ağaç görünümünün kullanıcıiçin karmaşık hiyerarşik bir seçenek seçeneği görüntülediğini varsayalım. Temel veriler büyükse, kullanıcı uygulamada başka bir şeyle ilgili olduğunda ağacı bellekte tutmak verimsizdir.  
  
 Kullanıcı uygulamanın başka bir bölümüne geçtiğinde, <xref:System.WeakReference> ağaca zayıf bir başvuru oluşturmak ve tüm güçlü başvuruları yok etmek için sınıfı kullanabilirsiniz. Kullanıcı ağaca geri döndüğünde, uygulama ağaca güçlü bir başvuru elde etmeye çalışır ve başarılı olursa, ağacı yeniden yapılandırmaktan kaçınır.  
  
 Bir nesneyle zayıf bir başvuru oluşturmak <xref:System.WeakReference> için, izlenecek nesnenin örneğini kullanarak bir nesne oluşturursunuz. Daha sonra <xref:System.WeakReference.Target%2A> özelliği bu nesneye ayarlarsınız ve nesnenin özgün başvurusu `null`'nu . Kod örneği için <xref:System.WeakReference> sınıf kitaplığına bakın.  
  
## <a name="short-and-long-weak-references"></a>Kısa ve Uzun Zayıf Referanslar  
 Kısa zayıf bir başvuru veya uzun zayıf bir başvuru oluşturabilirsiniz:  
  
- Kısa  
  
     Kısa zayıf bir başvurunun `null` hedefi, nesne çöp toplama tarafından geri kazanıldığında olur. Zayıf başvuru nun kendisi yönetilen bir nesnedir ve diğer yönetilen nesne gibi çöp toplamaya tabidir.  Kısa zayıf bir referans için <xref:System.WeakReference>parametresiz yapıcıdır.  
  
- Uzun  
  
     Nesnenin <xref:System.Object.Finalize%2A> yöntemi çağrıldıktan sonra uzun zayıf bir başvuru korunur. Bu, nesnenin yeniden oluşturulmasına izin verir, ancak nesnenin durumu öngörülemez kalır. Uzun bir başvuru kullanmak `true` için, oluşturucu belirtin. <xref:System.WeakReference>  
  
     Nesnenin türünde bir <xref:System.Object.Finalize%2A> yöntem yoksa, kısa zayıf başvuru işlevi uygulanır ve zayıf başvuru yalnızca hedef toplanana kadar geçerlidir ve bu da sonlandırıcı çalıştırıldıktan sonra her zaman oluşabilir.  
  
 Güçlü bir başvuru oluşturmak ve nesneyi <xref:System.WeakReference.Target%2A> yeniden kullanmak <xref:System.WeakReference> için, a özelliğini nesnenin türüne atın. <xref:System.WeakReference.Target%2A> Özellik dönerse, `null`nesne toplandı; aksi takdirde, uygulama ona güçlü bir başvuru kazandı, çünkü nesneyi kullanmaya devam edebilirsiniz.  
  
## <a name="guidelines-for-using-weak-references"></a>Zayıf Referansları Kullanma Yönergeleri  
 Yalnızca nesnenin durumu sonlandırmadan sonra öngörülemez olduğu için gerektiğinde uzun zayıf başvurular kullanın.  
  
 İşaretçinin kendisi büyük veya daha büyük olabileceğinden, küçük nesnelere zayıf başvurular kullanmaktan kaçının.  
  
 Zayıf başvuruları bellek yönetimi sorunlarına otomatik bir çözüm olarak kullanmaktan kaçının. Bunun yerine, uygulamanızın nesnelerini işlemek için etkili bir önbelleğe alma ilkesi geliştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çöp Toplama](../../../docs/standard/garbage-collection/index.md)
