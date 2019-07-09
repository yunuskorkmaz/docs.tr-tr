---
title: Yönetilmeyen Kaynakları Temizleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6be45a3d03d8cff580653260081a20d518448237
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662727"
---
# <a name="cleaning-up-unmanaged-resources"></a>Yönetilmeyen Kaynakları Temizleme

Uygulamanızın oluşturduğu nesnelerin çoğu için üzerinde güvenebilirsiniz. Bellek yönetimi işlemede NET'in çöp toplayıcı. Ancak, yönetilmeyen kaynaklar içeren nesneler oluşturduğunuzda, uygulamanızda kullanmayı bitirdiğinizde, bu kaynakları açıkça serbest bırakmanız gerekir. En sık karşılaşılan yönetilmeyen kaynak türleri, dosyalar, pencereler, ağ bağlantıları veya veritabanı bağlantıları gibi işletim sistemi kaynaklarını saran nesnelerdir. Çöp toplayıcı yönetilmeyen bir kaynağı kapsülleyen bir nesnenin kullanım ömrünü izleyebilir olsa da, yönetilmeyen kaynağı nasıl serbest bırakacağını ve temizleyeceğini bilmez.

Türleriniz yönetilmeyen kaynaklar ise, aşağıdakileri yapmanız gerekir:

- Uygulama [dispose deseni](../../../docs/standard/design-guidelines/dispose-pattern.md). Bu sağlamanızı ister bir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> yönetilmeyen kaynakların belirli şekilde serbest bırakılmasını etkinleştirmek için uygulama. Bir tüketici türü çağrılarınızı, <xref:System.IDisposable.Dispose%2A> zaman nesnesi (ve kullandığı kaynaklar) artık gerekli. <xref:System.IDisposable.Dispose%2A> Yöntemi yönetilmeyen kaynakları hemen serbest bırakır.

- Yönetilmeyen kaynaklarınızı çağrılacak türünüzün bir tüketicisi unutması durumunda, yayımlanabilmesine olanak sağlayan <xref:System.IDisposable.Dispose%2A>. Bunu yapmak için iki yol vardır:

  - Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı kullanın. Önerilen yöntem budur. Güvenli tanıtıcılar türetilir <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı ve güçlü bir dahil <xref:System.Object.Finalize%2A> yöntemi. Güvenli bir tanıtıcı kullandığınızda, yalnızca uygulamanız <xref:System.IDisposable> arabirim ve güvenli tanıtıcınızın çağrı <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> yönteminde, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması. Güvenli tanıtıcının Sonlandırıcısı otomatik olarak atık toplayıcı tarafından çağrılır, <xref:System.IDisposable.Dispose%2A> yöntemi çağrılmadı.

    —veya—

  - Geçersiz kılma <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. Sonlandırma yönetilmeyen kaynakların belirli olmayan şekilde serbest çağırmak bir tür tüketici başarısız olduğunda sağlayan <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> onları belirsiz şekilde atmak için. Ancak, nesne sonlandırma karmaşık ve hataya açık bir işlem olduğundan, kendi sonlandırıcınızı sağlamak yerine güvenli tanıtıcı kullanmanız önerilir.

Türünüzün tüketicileri daha sonra çağırabilir, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> doğrudan yönetilmeyen kaynaklar tarafından kullanılan belleği serbest bırakmak. Doğru şekilde uyguladığınızda bir <xref:System.IDisposable.Dispose%2A> yöntemi, ya da güvenli tanıtıcınızın <xref:System.Object.Finalize%2A> yöntemi veya geçersiz kılan kendi <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi kaynakları temizlemek için bir önlem haline gelir durumunda <xref:System.IDisposable.Dispose%2A> yöntemi çağrılmadı.

## <a name="in-this-section"></a>Bu Bölümde

[Implementing a Dispose Method](../../../docs/standard/garbage-collection/implementing-dispose.md) nasıl uygulanacağını açıklar [dispose deseni](../../../docs/standard/design-guidelines/dispose-pattern.md) yönetilmeyen kaynakları serbest bırakmak.

[Nesneleri, IDisposable'ı kullanarak](../../../docs/standard/garbage-collection/using-objects.md) nasıl bir türün tüketicilerinin sağlayacaklarını açıklar, <xref:System.IDisposable.Dispose%2A> uygulama çağrılır. Kullanmanızı öneririz C# `using` deyimi veya Visual Basic `Using` Bunu yapmak için deyimi.

## <a name="reference"></a>Başvuru

<xref:System.IDisposable?displayProperty=nameWithType>\
Tanımlar <xref:System.IDisposable.Dispose%2A> yöntemi yönetilmeyen kaynakları serbest bırakmak.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Tarafından yönetilmeyen kaynakları serbest bırakılmazsa, nesne sonlandırması sağlar <xref:System.IDisposable.Dispose%2A> yöntemi.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Sonlandırmayı bastırır. Yönteminden özel olarak bu yöntem çağrılır bir `Dispose` bir sonlandırıcının yürütülmesini önlemek için yöntemi.
