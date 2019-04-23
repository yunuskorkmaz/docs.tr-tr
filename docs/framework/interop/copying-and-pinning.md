---
title: Kopyalama ve Sabitleme
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1696bd6eb4eb3a43593cf7ed264c80745c1ec66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326287"
---
# <a name="copying-and-pinning"></a>Kopyalama ve Sabitleme
Veri sıralarken, birlikte çalışma sıralayıcısı kopyalayabilir veya sıralanmış veri sabitleyin. Veri kopyalama verilerin bir kopyasını başka bir bellek konumuna bir bellek konumunda yerleştirir. Bir değer türü kopyalama arasındaki farklar aşağıda gösterilmiştir ve bir tür kopyalama başvuruya göre yönetilmeyen bellek yönetilen geçirilmedi.  
  
 ![Değer ve başvuru türleri nasıl kopyalanır gösteren diyagram.](./media/copying-and-pinning/interop-marshal-copy.gif)  
  
 Değer olarak geçilemez yöntem bağımsız değişkenleri yığında değerler olarak yönetilmeyen kod için hazırlanırlar. Kopyalama işlemi doğrudan. Gibi işaretçiler, başvuruya göre geçirilen bağımsız değişkenler yığında geçirilir. Başvuru türleri de değere ve başvuruya göre iletilir. Aşağıdaki çizimde gösterildiği gibi değer olarak geçilemez başvuru türleri ya da kopyaladığınız Sabitlenen veya: 
  
 ![Diyagram gösteren başvuru türleri, değere ve başvuruya göre geçirilen.](./media/copying-and-pinning/interop-marshal-reference-pin.gif)  
  
 Geçici olarak sabitleme, bu nedenle ortak dil çalışma zamanının atık toplayıcısı tarafından yeniden konumlandırılması tutma geçerli bellek konumuna verileri kilitler. Sıralayıcı, veri kopyalama yükünü azaltmak ve performansı artırmak için sabitler. Veri türü kopyaladığınız veya sıralama işlemi sırasında sabitlenmiş olup olmadığını belirler.  Sabitleme otomatik olarak gerçekleştirilir gibi nesneler için sıralama sırasında <xref:System.String>bellek kullanarak el ile de sabitleyebilirsiniz ancak <xref:System.Runtime.InteropServices.GCHandle> sınıfı.  
  
## <a name="formatted-blittable-classes"></a>Biçimlendirilmiş Blittable sınıfları  
 Biçimlendirilmiş [blittable](blittable-and-non-blittable-types.md) sınıfları (biçimlendirilmiş) düzeni sabit ve ortak veri temsilini hem yönetilen hem de yönetilmeyen bellek. Bu tür hazırlama gerektirdiğinde yığındaki bir nesneye bir işaretçi çağrılanın doğrudan geçirilir. Çağrılan bellek konumuna işaretçi tarafından başvurulan içeriği değiştirebilirsiniz.  
  
> [!NOTE]
>  Out veya In/Out parametresi işaretlenmişse çağrılan bellek içeriği değiştirebilirsiniz. Buna karşılık, çağrılan parametresi gibi sıralamakta ayarlandığında içeriğini değiştirme biçimlendirilmiş bir blok halinde kopyalanabilir türler için varsayılan kaçınmanız gerekir. In nesneyi değiştirme aynı sınıf için bir tür kitaplığı dışarı aktarılırken sorunları oluşturur ve çapraz-grup çağrıları yapmak için kullanılır.  
  
## <a name="formatted-non-blittable-classes"></a>Biçimlendirilmiş Blittable olmayan sınıflar  
 Biçimlendirilmiş [kopyalanamaz](blittable-and-non-blittable-types.md) sınıfları (biçimlendirilmiş) düzeni sabit ancak veri temsilini yönetilen ve yönetilmeyen bellekte farklıdır. Veri dönüştürme aşağıdaki koşullarda gerektirebilir:  
  
-   Blittable olmayan sınıf değere göre sıralanmış olduğundan çağrılan bir kopyasını bir veri yapısına bir işaretçi alır.  
  
-   Blittable olmayan sınıf başvuruya göre sıralanmış olduğundan çağrılan bir kopyasını veri yapısı işaretçisi için bir işaretçi alır.  
  
-   Varsa <xref:System.Runtime.InteropServices.InAttribute> özniteliği, bu kopyanın her zaman gerektiği şekilde hazırlama, örneğin durumu ile başlatılır.  
  
-   Varsa <xref:System.Runtime.InteropServices.OutAttribute> özniteliği, durumu her zaman sonrasında, gerektiği şekilde hazırlama örneğine geri kopyalanır.  
  
-   Her iki **InAttribute** ve **OutAttribute** , her iki kopyasında gerekli ayarlanmıştır. Her iki öznitelik belirtilmezse, ya da kopyalama ortadan kaldırarak Sıralayıcı iyileştirebilirsiniz.  
  
## <a name="reference-types"></a>Başvuru Türleri  
 Başvuru türleri, değer veya başvuruya göre geçirilebilir. Değere göre geçirildiğinde türü bir işaretçi yığında geçirilir. Başvuruya göre geçirildiği durumların bir işaretçi türüne bir işaretçi yığında geçirilir.  
  
 Başvuru türleri aşağıdaki koşullu davranışı vardır:  
  
-   Türleri, bir başvuru türü değerle geçirilir ve kopyalanamaz türlerin üyelerini varsa, iki kez dönüştürülür:  
  
    -   Ne zaman bir bağımsız değişken yönetilmeyen tarafa geçirilir.  
  
    -   Geri çağrısından.  
  
     Önlemek için gereksiz yere kopyalayarak ve dönüştürme, bu tür olarak sıralanmış parametreleri. Açıkça uygulamalısınız **InAttribute** ve **OutAttribute** öznitelikleri için Aranan tarafından yapılan değişiklikleri görmek arayan için bağımsız değişken.  
  
-   Bir başvuru türü değerle geçirilir ve yalnızca blittable türlerinde üyeler varsa, hazırlama sırasında sabitlenebilir ve tür üyeleri için Aranan tarafından yapılan değişiklikler arayan tarafından görülür. Uygulama **InAttribute** ve **OutAttribute** açıkça bu davranışı istiyorsanız. Bu yönlü öznitelikler, tür kitaplığına yönlü bilgilerini birlikte çalışma sıralayıcısı vermez (Bu gibi varsayılan dışarı aktarır) ve bu COM çapraz-grup sıralama ile sorunlara neden olabilir.  
  
-   Başvuruya göre bir başvuru türü geçirilmezse, bu In/Out varsayılan olarak sıralanmış.  
  
## <a name="systemstring-and-systemtextstringbuilder"></a>System.String ve System.Text.StringBuilder  
 Veri yönetilmeyen koda değere veya başvuruya göre sıralanır, Sıralayıcı, genellikle verileri (büyük olasılıkla karakter kümesi, kopyalama sırasında dönüştürme) bir ikincil arabelleğe kopyalar ve çağrılanın arabellek bir başvuru geçirir. Başvuru olmadığı sürece bir **BSTR** ile ayrılan **SysAllocString**, başvuru ile her zaman ayrılır **CoTaskMemAlloc**.  
  
 Ya da dize türü (örneğin, Unicode karakter dizesi gibi) değerine göre sıralanmış bir iyileştirme Sıralayıcı çağrılan doğrudan bir işaretçi için yeni bir arabellek kopyalamak yerine iç Unicode arabellek yönetilen dizelere geçer.  
  
> [!CAUTION]
>  Bir dize değeriyle geçirildiğinde, çağrılan hiçbir zaman sıralayıcı tarafından geçirilen başvuru değiştirmeniz gerekir. Bunun yapılması, yönetilen yığın bozabilir.  
  
 Olduğunda bir <xref:System.String?displayProperty=nameWithType> geçirilen başvuruya göre sıralayıcı içeriğini dize için ikincil bir arabellek çağrı yapmadan önce kopyalar. Ardından çağrısından dönüşte, yeni bir dizeye arabellek içeriğini kopyalar. Bu teknik, yönetilen bir değişmez dize değiştirilmemiş kalmasını sağlar.  
  
 Olduğunda bir <xref:System.Text.StringBuilder?displayProperty=nameWithType> değeri, Sıralayıcı geçişleri iç arabellek başvuru tarafından geçirilen **StringBuilder** doğrudan çağırana. Çağıran ve çağrılan arabellek boyutuna kabul etmesi gerekir. Çağıranın oluşturmaktan sorumlu bir **StringBuilder** yeterli uzunluğu. Çağrılan arabellek değil taşması emin olmak için gerekli önlemleri almanız gerekir. **StringBuilder** olduğundan başvuru türleri değer olarak geçilemez kural için bir özel parametre olduğu gibi varsayılan olarak geçirilir. Bu her zaman geçirilir olarak daraltma veya genişletme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)
- [Yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Birlikte Çalışma için Hazırlama](interop-marshaling.md)
