---
title: Kopyalama ve Sabitleme
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
ms.openlocfilehash: f6db7d37293015911c1285d39e19bf7542a7ac59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123636"
---
# <a name="copying-and-pinning"></a>Kopyalama ve Sabitleme

Verileri sıralama sırasında birlikte çalışma sıralayıcısı, sıralanan verileri kopyalayabilir veya sabitleyebilir. Verilerin kopyalanması, verilerin bir kopyasını başka bir bellek konumundaki bir bellek konumundan bir konuma koyar. Aşağıdaki çizimde, bir değer türü kopyalama ve bir başvuruya göre geçirilen bir tür ile yönetilmeyen belleğe kopyalama arasındaki farklar gösterilmektedir.

![Değer ve başvuru türlerinin nasıl kopyalanacağını gösteren diyagram.](./media/copying-and-pinning/interop-marshal-copy.gif)

Değer tarafından geçirilen yöntem bağımsız değişkenleri, yığın üzerinde değer olarak yönetilmeyen koda sıralanır. Kopyalama işlemi doğrudan olur. Başvuruya göre geçirilen bağımsız değişkenler yığına işaretçiler olarak geçirilir. Başvuru türleri de değere ve başvuruya göre geçirilir. Aşağıdaki çizimde gösterildiği gibi, değer tarafından geçirilen başvuru türleri kopyalanır veya sabitlenir:

![Değere ve başvuruya göre geçirilen başvuru türlerini gösteren diyagram.](./media/copying-and-pinning/interop-marshal-reference-pin.gif)

Veri sabitleme, verileri geçerli bellek konumunda geçici olarak kilitler ve bu sayede ortak dil çalışma zamanının çöp toplayıcısının yeniden konumlandırılmasını sağlar. Sıralayıcı, performansı kopyalama ve geliştirme yükünü azaltmak için verileri sabitler. Verilerin türü, sıralama işlemi sırasında kopyalanıp kopyalanmadığını veya sabitlenmeyeceğini belirler.  Sabitleme işlemi, <xref:System.String>gibi nesneler için sıralama sırasında otomatik olarak gerçekleştirilir, ancak <xref:System.Runtime.InteropServices.GCHandle> sınıfını kullanarak belleği el ile sabitleyebilirsiniz.

## <a name="formatted-blittable-classes"></a>Biçimlendirilen blittable sınıfları

Biçimlendirilen [blittable](blittable-and-non-blittable-types.md) sınıflarının hem yönetilen hem de yönetilmeyen bellekte sabit düzeni (biçimli) ve ortak veri temsili vardır. Bu türler sıralama gerektirdiğinde, yığında nesne işaretçisi doğrudan çağrıa geçirilir. Aranan, işaretçinin başvurduğu bellek konumunun içeriğini değiştirebilir.

> [!NOTE]
> Parametre dışarı veya dışarı işaretlenmişse, çağrılan bellek içeriğini değiştirebilir. Buna karşılık, parametresi ' de olarak sıralama olarak ayarlandığında, aranan blittable türleri için varsayılan değer olan, aranan içeriği değiştirmekten kaçınmalıdır. Bir ın nesnesini değiştirmek, aynı sınıf bir tür kitaplığına aktarıldığında ve çapraz grup çağrıları yapmak için kullanıldığında sorunlar oluşturur.

## <a name="formatted-non-blittable-classes"></a>Blittable olmayan sınıflar biçimlendirildi

Biçimlendirilen [non-blittable](blittable-and-non-blittable-types.md) sınıfları sabit düzene sahip (biçimlendirildi), ancak veri gösterimi yönetilen ve yönetilmeyen bellekte farklıdır. Veriler aşağıdaki koşullarda Dönüşüm gerektirebilir:

- Blittable olmayan bir sınıf değere göre sıralandıysanız, çağrılan, veri yapısının bir kopyasına bir işaretçi alır.

- Blittable olmayan bir sınıf başvuruya göre sıralandıysanız, çağrılan, veri yapısının bir kopyasına yönelik bir işaretçi alır.

- <xref:System.Runtime.InteropServices.InAttribute> özniteliği ayarlandıysa, bu kopya her zaman örneğin durumuyla başlatılır ve gerektiğinde sıralama yapılır.

- <xref:System.Runtime.InteropServices.OutAttribute> özniteliği ayarlandıysa, durum her zaman döndürülen örneğe geri kopyalanır ve gerektiğinde sıralama yapılır.

- **InAttribute** ve **OutAttribute** öğelerinin her ikisi de ayarlanırsa, her iki kopya de gereklidir. Her iki öznitelik de atlanırsa Sıralayıcı, kopyayı ortadan kaldırarak iyileştirebilirler.

## <a name="reference-types"></a>Başvuru Türleri

Başvuru türleri, değere veya başvuruya göre geçirilebilir. Değer ile geçirildiğinde, yığına tür işaretçisi geçirilir. Başvuruya göre geçirildiğinde, tür işaretçisine bir işaretçi yığına geçirilir.

Başvuru türleri aşağıdaki koşullu davranışa sahiptir:

- Bir başvuru türü değere göre geçirilir ve blittable olmayan türlerde üyelere sahipse türler iki kez dönüştürülür:

  - Yönetilmeyen tarafa bir bağımsız değişken geçirildiğinde.

  - Çağrıdan geri dönün.

  Gereksiz kopyalama ve dönüştürmeyi önlemek için bu türler parametrelerde olduğu gibi sıralanır. Çağıran tarafından yapılan değişiklikleri görmek için bir bağımsız değişkene **InAttribute** ve **OutAttribute** özniteliklerini açıkça uygulamanız gerekir.

- Bir başvuru türü değere göre geçirilmişse ve yalnızca blittable türlerin üyeleri içeriyorsa, sıralama sırasında sabitlenebilir ve aranan tarafından tür üyelerinde yapılan değişiklikler arayan tarafından görülür. Bu davranışı isterseniz **InAttribute** ve **OutAttribute** 'ı açık bir şekilde uygulayın. Bu yönlü öznitelikler olmadan, birlikte çalışma sıralayıcısı yönlü bilgileri tür kitaplığına dışa aktarmaz (varsayılan olan ' de olarak dışa aktarır) ve bu, COM çapraz grup sıralaması ile ilgili sorunlara neden olabilir.

- Başvuru türü başvuru ile geçirilmezse, varsayılan olarak Içinde/dışarı olarak sıralanır.

## <a name="systemstring-and-systemtextstringbuilder"></a>System. String ve System. Text. StringBuilder

Veriler, değere veya başvuruya göre yönetilmeyen koda sıralandığında, Sıralayıcı tipik olarak verileri ikincil bir arabelleğe kopyalar (büyük olasılıkla kopya sırasında karakter kümelerini dönüştürüyor) ve bir arabelleğe bir başvuru çağırarak aranan öğesine geçirir. Başvuru, **SysAllocString**ile ayrılmış bir **BSTR** değilse, başvuru her zaman **CoTaskMemAlloc**ile ayrılır.

Dize türü değere göre sıralanmışsa (örneğin, bir Unicode karakter dizesi), Sıralayıcı çağıran, iç Unicode arabelleğinde yönetilen dizelere doğrudan bir işaretçi ekleyerek onu yeni bir arabelleğe kopyalamanız gerekir.

> [!CAUTION]
> Bir dize değere göre geçirildiğinde, çağrılan, Sıralayıcı tarafından geçirilen başvuruyu hiçbir zaman değiştirmemelidir. Bunun yapılması yönetilen yığının bozulmasına neden olabilir.

Bir <xref:System.String?displayProperty=nameWithType> başvuruya göre geçirildiğinde Sıralayıcı, çağrıyı yapmadan önce, içeriği ikincil arabelleğe kopyalar. Ardından, arabelleğin içeriğini çağrıdan dönüşte yeni bir dizeye kopyalar. Bu teknik, sabit yönetilen dizenin değiştirilmemiş olarak kalmasını sağlar.

Değer tarafından <xref:System.Text.StringBuilder?displayProperty=nameWithType> geçirildiğinde Sıralayıcı, **StringBuilder** 'ın iç arabelleğine doğrudan çağırana bir başvuru geçirir. Çağıran ve çağrılan, arabelleğin boyutunu kabul etmelidir. Çağıran, yeterli uzunlukta bir **StringBuilder** oluşturmaktan sorumludur. Aranan, arabelleğin taşma olmamasını sağlamak için gerekli önlemleri almalıdır. **StringBuilder** , değere göre geçirilen başvuru türleri varsayılan olarak parametrelerde olarak geçirilir kural için bir özel durumdur. Her zaman Içinde/dışarı olarak geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)
- [Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Birlikte Çalışma için Hazırlama](interop-marshaling.md)
