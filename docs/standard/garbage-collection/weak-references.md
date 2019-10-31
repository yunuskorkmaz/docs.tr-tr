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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141336"
---
# <a name="weak-references"></a>Zayıf Başvurular
Çöp toplayıcı, uygulamanın kodu bu nesneye ulaşabilirken bir uygulama tarafından kullanılan bir nesneyi toplayamıyor. Uygulamanın nesneye güçlü bir başvurusu olduğu söylenir.  
  
 Zayıf bir başvuru, uygulamanın nesneye erişmesine hala izin verirken çöp toplayıcısının nesneyi toplamasını sağlar. Zayıf bir başvuru yalnızca, kesin bir başvuru olmadığında nesne toplanana kadar belirsiz süre boyunca geçerlidir. Zayıf bir başvuru kullandığınızda, uygulama nesneye bir güçlü başvuru elde edebilir ve bu da toplanmasını önler. Ancak, güçlü bir başvurunun yeniden kurulmadan önce çöp toplayıcının nesneye her zaman ulaşmak her zaman risk vardır.  
  
 Zayıf başvurular, çok fazla bellek kullanan nesneler için yararlıdır ancak çöp toplama tarafından geri kazanıladıklarında kolayca yeniden oluşturulabilir.  
  
 Bir Windows Forms uygulamasındaki ağaç görünümünün, kullanıcıya karmaşık hiyerarşik bir seçenek seçeneği olduğunu varsayalım. Temel alınan veriler büyükse, Kullanıcı uygulamada başka bir şeyle ilişkili olduğunda ağacın bellekte tutulması verimsiz olur.  
  
 Kullanıcı uygulamanın başka bir kısmına geçtiğinde, ağaca zayıf bir başvuru oluşturmak ve tüm güçlü başvuruları yok etmek için <xref:System.WeakReference> sınıfını kullanabilirsiniz. Kullanıcı ağaca geri geçtiğinde, uygulama ağaca güçlü bir başvuru edinmeye çalışır ve başarılı olursa ağacın yeniden çözümlenmesini önler.  
  
 Bir nesneyle zayıf bir başvuru oluşturmak için, izlenecek nesnenin örneğini kullanarak bir <xref:System.WeakReference> oluşturursunuz. Sonra <xref:System.WeakReference.Target%2A> özelliğini bu nesneye ayarlarsınız ve nesneye özgün başvuruyu `null`olarak ayarlarsınız. Kod örneği için bkz. sınıf kitaplığındaki <xref:System.WeakReference>.  
  
## <a name="short-and-long-weak-references"></a>Kısa ve uzun zayıf başvurular  
 Kısa bir zayıf başvuru veya uzun bir zayıf başvuru oluşturabilirsiniz:  
  
- Kısadır  
  
     Kısa bir zayıf başvurunun hedefi, nesne çöp toplama tarafından geri kazanılır `null` olur. Zayıf başvuru, yönetilen bir nesnedir ve aynı diğer yönetilen nesneler gibi çöp toplamaya tabidir.  Kısa bir zayıf başvuru, <xref:System.WeakReference>parametresiz oluşturucudur.  
  
- Kalacağını  
  
     Nesnenin <xref:System.Object.Finalize%2A> yöntemi çağrıldıktan sonra uzun bir zayıf başvuru tutulur. Bu, nesnenin yeniden oluşturulmasına izin verir, ancak nesnenin durumu öngörülemeyen olarak kalır. Uzun bir başvuru kullanmak için <xref:System.WeakReference> oluşturucuda `true` belirtin.  
  
     Nesnenin türünün bir <xref:System.Object.Finalize%2A> yöntemi yoksa, kısa zayıf başvuru işlevselliği uygulanır ve zayıf başvuru yalnızca hedef toplanana kadar geçerlidir. Bu, Sonlandırıcı çalıştıktan sonra herhangi bir zamanda gerçekleşebilir.  
  
 Güçlü bir başvuru oluşturmak ve nesneyi tekrar kullanmak için, bir <xref:System.WeakReference> <xref:System.WeakReference.Target%2A> özelliğini nesnenin türüne atayın. <xref:System.WeakReference.Target%2A> özelliği `null`döndürürse, nesne toplanmıştı; Aksi takdirde, uygulama kendisine güçlü bir başvuru içerdiğinden nesnesini kullanmaya devam edebilirsiniz.  
  
## <a name="guidelines-for-using-weak-references"></a>Zayıf başvuruları kullanmaya yönelik yönergeler  
 Yalnızca nesnenin durumu sonlandıralındıktan sonra tahmin edildiğinde uzun zayıf başvuruları kullanın.  
  
 Küçük nesnelere zayıf başvurular kullanmaktan kaçının çünkü işaretçinin kendisi büyük veya daha büyük olabilir.  
  
 Bellek yönetimi sorunlarına otomatik çözüm olarak zayıf başvuruları kullanmaktan kaçının. Bunun yerine, uygulamanızın nesnelerini işlemeye yönelik etkili bir önbelleğe alma ilkesi geliştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
