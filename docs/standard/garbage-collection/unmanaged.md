---
title: "Yönetilmeyen Kaynakları Temizleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c94a449edbbe38c4028e27fd946b66a054badf51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cleaning-up-unmanaged-resources"></a>Yönetilmeyen Kaynakları Temizleme
Uygulamanızın oluşturduğu nesneler çoğunluğu için üzerinde güvenebilirsiniz. Bellek yönetimi işlemek için NET'in atık toplayıcı. Ancak, yönetilmeyen kaynaklar içeren nesneler oluşturduğunuzda, uygulamanızda kullanmayı bitirdiğinizde, bu kaynakları açıkça serbest bırakmanız gerekir. En sık karşılaşılan yönetilmeyen kaynak türleri, dosyalar, pencereler, ağ bağlantıları veya veritabanı bağlantıları gibi işletim sistemi kaynaklarını saran nesnelerdir. Çöp toplayıcı yönetilmeyen bir kaynağı kapsülleyen bir nesnenin kullanım ömrünü izleyebilir olsa da, yönetilmeyen kaynağı nasıl serbest bırakacağını ve temizleyeceğini bilmez.  
  
 Türleriniz yönetilmeyen kaynaklar ise, aşağıdakileri yapmanız gerekir:  
  
-   Uygulama [düzeni dispose](../../../docs/standard/design-guidelines/dispose-pattern.md). Bu sağlamanızı ister bir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> yönetilmeyen kaynakları belirleyici sürümü etkinleştirmek için uygulama. Türü çağrılarınızı tüketicisi <xref:System.IDisposable.Dispose%2A> zaman nesnesi (ve kaynaklarını) artık gerekli. <xref:System.IDisposable.Dispose%2A> Yöntemi hemen yönetilmeyen kaynakları serbest bırakır.  
  
-   Yönetilmeyen kaynaklarınızı çağırmak bir tüketici türünüze unutması durumunda, serbest bırakılacak sağlamak <xref:System.IDisposable.Dispose%2A>. Bunu yapmak için iki yol vardır:  
  
    -   Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı kullanın. Önerilen yöntem budur. Güvenli tanıtıcıları türetilir <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı ve sağlam bir dahil <xref:System.Object.Finalize%2A> yöntemi. Güvenli bir tanıtıcı kullandığınızda, yalnızca uygulamanız <xref:System.IDisposable> arabirim ve güvenli tanıtıcının çağrısı <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> yönteminde, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması. Varsa güvenli tutamacın sonlandırıcıyı otomatik olarak atık toplayıcısı tarafından çağrılır, <xref:System.IDisposable.Dispose%2A> yöntemi çağrılmaz.  
  
         —veya—  
  
    -   Geçersiz kılma <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. Sonlandırma etkinleştirir yönetilmeyen kaynakları belirleyici olmayan sürümü çağırmak bir tür tüketici başarısız olduğunda <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bunları belirleyici biçimde silmek için. Ancak, nesne sonlandırma karmaşık ve hataya açık bir işlem olduğundan, kendi sonlandırıcınızı sağlamak yerine güvenli tanıtıcı kullanmanız önerilir.  
  
 Tüketiciler türünüze sonra çağırabilir, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> doğrudan yönetilmeyen kaynaklar tarafından kullanılan belleği boşaltmak için uygulama. Ne zaman düzgün uygulamanız bir <xref:System.IDisposable.Dispose%2A> yöntemi, ya da güvenli tanıtıcının <xref:System.Object.Finalize%2A> yöntemini veya kendi geçersiz kılma <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi kaynakları temizlemek için koruyucu olur durumunda <xref:System.IDisposable.Dispose%2A> yöntemi çağrılmaz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Dispose yöntemi uygulama](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 Nasıl uygulandığı açıklanır [düzeni dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) yönetilmeyen kaynakları serbest bırakmak için.  
  
 [IDisposable uygulayan nesneler kullanma](../../../docs/standard/garbage-collection/using-objects.md)  
 Nasıl bir türde tüketicileri emin açıklar kendi <xref:System.IDisposable.Dispose%2A> uygulaması çağrılır. C# kullanarak öneririz `using` deyimi veya Visual Basic `Using` Bunu yapmak için deyimi.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 Tanımlar <xref:System.IDisposable.Dispose%2A> yönetilmeyen kaynakları serbest bırakmak için yöntem.  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 Tarafından yönetilmeyen kaynakları serbest bırakılmaz nesne sonlandırma sağlar <xref:System.IDisposable.Dispose%2A> yöntemi.  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 Sonlandırmayı bastırır. Bu yöntem geleneksel yönteminden çağrılan bir `Dispose` bir sonlandırıcı yürütülmesini engellemek için yöntem.
