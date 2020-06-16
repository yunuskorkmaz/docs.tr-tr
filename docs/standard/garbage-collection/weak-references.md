---
title: Zayıf Başvurular
description: .NET Atık toplayıcısının, uygulamanın nesneye erişmesine izin verirken bir nesne toplamasına izin veren zayıf başvurular hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
ms.openlocfilehash: 1c18b4fa979058893e0683620ec6cff8e7b15b9b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768189"
---
# <a name="weak-references"></a>Zayıf Başvurular
Çöp toplayıcı, uygulamanın kodu bu nesneye ulaşabilirken bir uygulama tarafından kullanılan bir nesneyi toplayamıyor. Uygulamanın nesneye güçlü bir başvurusu olduğu söylenir.  
  
 Zayıf bir başvuru, uygulamanın nesneye erişmesine hala izin verirken çöp toplayıcısının nesneyi toplamasını sağlar. Zayıf bir başvuru yalnızca, kesin bir başvuru olmadığında nesne toplanana kadar belirsiz süre boyunca geçerlidir. Zayıf bir başvuru kullandığınızda, uygulama nesneye bir güçlü başvuru elde edebilir ve bu da toplanmasını önler. Ancak, güçlü bir başvurunun yeniden kurulmadan önce çöp toplayıcının nesneye her zaman ulaşmak her zaman risk vardır.  
  
 Zayıf başvurular, çok fazla bellek kullanan nesneler için yararlıdır ancak çöp toplama tarafından geri kazanıladıklarında kolayca yeniden oluşturulabilir.  
  
 Bir Windows Forms uygulamasındaki ağaç görünümünün, kullanıcıya karmaşık hiyerarşik bir seçenek seçeneği olduğunu varsayalım. Temel alınan veriler büyükse, Kullanıcı uygulamada başka bir şeyle ilişkili olduğunda ağacın bellekte tutulması verimsiz olur.  
  
 Kullanıcı uygulamanın başka bir kısmına geçtiğinde, <xref:System.WeakReference> ağaca bir zayıf başvuru oluşturmak ve tüm güçlü başvuruları yok etmek için sınıfını kullanabilirsiniz. Kullanıcı ağaca geri geçtiğinde, uygulama ağaca güçlü bir başvuru edinmeye çalışır ve başarılı olursa ağacın yeniden çözümlenmesini önler.  
  
 Bir nesneyle zayıf bir başvuru oluşturmak için, <xref:System.WeakReference> izlenecek nesnenin örneğini kullanarak oluşturursunuz. Sonra <xref:System.WeakReference.Target%2A> Bu nesneye özelliği ayarlarsınız ve nesnesine özgün başvuruyu olarak ayarlarsınız `null` . Kod örneği için bkz <xref:System.WeakReference> . sınıf kitaplığı 'nda.  
  
## <a name="short-and-long-weak-references"></a>Kısa ve uzun zayıf başvurular  
 Kısa bir zayıf başvuru veya uzun bir zayıf başvuru oluşturabilirsiniz:  
  
- Kısadır  
  
     Kısa bir zayıf başvurunun hedefi, `null` nesne çöp toplama tarafından geri kazanılır hale gelir. Zayıf başvuru, yönetilen bir nesnedir ve aynı diğer yönetilen nesneler gibi çöp toplamaya tabidir.  Kısa bir zayıf başvuru, için parametresiz oluşturucudur <xref:System.WeakReference> .  
  
- Kalacağını  
  
     Nesnenin yöntemi çağrıldıktan sonra uzun bir zayıf başvuru tutulur <xref:System.Object.Finalize%2A> . Bu, nesnenin yeniden oluşturulmasına izin verir, ancak nesnenin durumu öngörülemeyen olarak kalır. Uzun bir başvuruyu kullanmak için oluşturucuda belirtin `true` <xref:System.WeakReference> .  
  
     Nesnenin türünün bir <xref:System.Object.Finalize%2A> yöntemi yoksa, kısa zayıf başvuru işlevselliği uygulanır ve zayıf başvuru yalnızca hedef toplanana kadar geçerlidir. Bu, Sonlandırıcı çalıştıktan sonra herhangi bir zamanda gerçekleşebilir.  
  
 Güçlü bir başvuru oluşturmak ve nesneyi tekrar kullanmak için, <xref:System.WeakReference.Target%2A> öğesinin özelliğini <xref:System.WeakReference> nesnesinin türüne atayın. <xref:System.WeakReference.Target%2A>Özelliği döndürürse `null` nesne toplanmıştı; Aksi takdirde, uygulama kendisine güçlü bir başvuru içerdiğinden nesneyi kullanmaya devam edebilirsiniz.  
  
## <a name="guidelines-for-using-weak-references"></a>Zayıf başvuruları kullanmaya yönelik yönergeler  
 Yalnızca nesnenin durumu sonlandıralındıktan sonra tahmin edildiğinde uzun zayıf başvuruları kullanın.  
  
 Küçük nesnelere zayıf başvurular kullanmaktan kaçının çünkü işaretçinin kendisi büyük veya daha büyük olabilir.  
  
 Bellek yönetimi sorunlarına otomatik çözüm olarak zayıf başvuruları kullanmaktan kaçının. Bunun yerine, uygulamanızın nesnelerini işlemeye yönelik etkili bir önbelleğe alma ilkesi geliştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çöp toplama](index.md)
