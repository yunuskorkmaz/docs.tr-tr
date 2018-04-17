---
title: Kopyalama ve Sabitleme
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c785c7bc9160cb252aad61fea00cce0d9a7eacdf
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="copying-and-pinning"></a>Kopyalama ve Sabitleme
Verileri hazırlama, birlikte çalışabilirlik Sıralayıcı kopyalayabilir veya sıralanmış veri sabitleyin. Veri kopyalama verilerin bir kopyasını tek bir yerden bellek başka bir bellek konuma yerleştirir. Bir değer türü kopyalama arasındaki farklar aşağıda gösterilmiştir ve bir tür kopyalama başvuruya göre yönetilmeyen bellek yönetilen geçirildi.  
  
 ![Değer türleri değer ve başvuru tarafından geçirilen](./media/interopmarshalcopy.gif "interopmarshalcopy")  
Değer ve başvuru tarafından geçirilen değer türleri  
  
 Yöntem bağımsız değişkenleri değere göre geçirilen yönetilmeyen koda yığında değerleri olarak hazırlanırlar. Kopyalama doğrudan bir işlemdir. Başvuruya göre geçirilen bağımsız değişkenler işaretçileri yığında geçirilir. Başvuru türleri de değer ve başvuru tarafından geçirilir. Aşağıdaki çizimde gösterildiği gibi değeri tarafından geçirilen başvuru türleri kopyalanan sabitlenmiş ya.  
  
 ![COM birlikte çalışma](./media/interopmarshalpin.gif "interopmarshalpin")  
Değer ve başvuru tarafından geçirilen başvuru türleri  
  
 Bu nedenle ortak dil çalışma zamanındaki atık toplayıcısı tarafından yeniden konumlandırılmasını tutma geçerli bellek konumuna verileri geçici olarak sabitleme kilitler. Sıralayıcı kopyalama yükünü azaltmak ve performansı geliştirmek için veri sabitler. Veri türü kopyaladığınız veya Hazırlama işlemi sırasında sabitlenmiş olup olmadığını belirler.  Sabitleme otomatik olarak gerçekleştirilir gibi nesneler için sıralama sırasında <xref:System.String>, bellek kullanarak el ile de sabitleyebilirsiniz ancak <xref:System.Runtime.InteropServices.GCHandle> sınıfı.  
  
## <a name="formatted-blittable-classes"></a>Biçimlendirilmiş Blittable sınıfları  
 Biçimlendirilmiş [blittable](blittable-and-non-blittable-types.md) sınıfları (biçimlendirilmiş) düzeni sabit ve hem de genel veri temsili yönetilen ve yönetilmeyen bellek. Bu tür hazırlama gerektirdiğinde, öbek nesnesinde bir işaretçi Aranan doğrudan geçirilir. Aranan işaretçiyi tarafından başvurulan bellek konumuna içeriğini değiştirebilirsiniz.  
  
> [!NOTE]
>  Çıkış veya giriş/çıkış parametresi işaretlenmişse Aranan bellek içeriğini değiştirebilirsiniz. Buna karşılık, aranan gibi sıralamakta parametresi ayarlandığında içeriğini değiştirme biçimlendirilmiş blittable türleri için varsayılan değer olan kaçınmalısınız. In nesneyi değiştirme aynı sınıf için bir tür kitaplığı dışarı aktardığınızda sorunları oluşturur ve arası grup çağrı yapmak için kullanılır.  
  
## <a name="formatted-non-blittable-classes"></a>Biçimlendirilmiş Blittable olmayan sınıfları  
 Biçimlendirilmiş [blittable olmayan](blittable-and-non-blittable-types.md) sınıfları (biçimlendirilmiş) düzeni sabit ancak veri temsili yönetilen ve yönetilmeyen bellekte farklıdır. Veri dönüştürme aşağıdaki koşullarda gerektirebilir:  
  
-   Blittable olmayan sınıf değerine göre sıralanmış, aranan veri yapısının bir işaretçi alır.  
  
-   Blittable olmayan sınıf başvuruya göre sıralanmış, aranan veri yapısının bir işaretçi bir işaretçi alır.  
  
-   Varsa <xref:System.Runtime.InteropServices.InAttribute> özniteliği olarak ayarlanmış, bu kopya her zaman gerektiği şekilde hazırlama örneğinin durumuyla başlatılır.  
  
-   Varsa <xref:System.Runtime.InteropServices.OutAttribute> özniteliği olarak ayarlanmışsa, durumu her zaman gerektiği şekilde hazırlama dönüşte örneğine kopyalanır.  
  
-   Her iki **InAttribute** ve **OutAttribute** , her iki kopya gerekli ayarlanmıştır. Her iki öznitelik atlanırsa, Sıralayıcı ya da kopyalama ortadan kaldırarak en iyi duruma getirebilirsiniz.  
  
## <a name="reference-types"></a>Başvuru Türleri  
 Başvuru türleri değere veya başvuruya göre geçirilebilir. Değere göre geçirildiğinde türü için bir işaretçi yığında geçirilir. Başvuruya göre geçirildiğinde türü için bir işaretçi bir işaretçi yığında geçirilir.  
  
 Başvuru türleri aşağıdaki koşullu davranışı vardır:  
  
-   Bir başvuru türü değeri geçirilir ve kopyalanamaz türler üyeleri sahipse, türleri iki kez dönüştürülür:  
  
    -   Ne zaman bir bağımsız değişken yönetilmeyen tarafa geçirilir.  
  
    -   Çağrısından getirisi.  
  
     Önlemek için gereksiz yere kopyalama ve dönüştürme, bu tür olarak sıralanmış parametreleri. Açıkça uygulamalısınız **InAttribute** ve **OutAttribute** öznitelikleri Aranan tarafından yapılan değişiklikleri görmek arayan için bağımsız değişken için.  
  
-   Bir başvuru türü değeri tarafından iletilir ve yalnızca blittable türleri üyeleri varsa, sıralama sırasında sabitlenmelidir ve türün üyeleri Aranan tarafından yapılan değişiklikler çağıran tarafından görülür. Uygulama **InAttribute** ve **OutAttribute** açıkça Bu davranış istiyorsanız. Tek yönlü özniteliklerden, tür kitaplığına yön bilgilerini birlikte çalışma Sıralayıcı vermez (bunu gibi varsayılan olan aktarır) ve bu COM arası grup sıralama ile ilgili sorunlara neden olabilir.  
  
-   Bir başvuru türü başvuruya göre aktarılırsa, olarak giriş/çıkış varsayılan olarak sıralanacağını.  
  
## <a name="systemstring-and-systemtextstringbuilder"></a>System.String ve System.Text.StringBuilder  
 Veri yönetilmeyen koda değere veya başvuruya göre sıralanmış olduğundan, Sıralayıcı, genellikle verileri (büyük olasılıkla karakter kümesi kopyalama sırasında dönüştürme) ikincil bir arabellek kopyalar ve arabellek başvuru Aranan geçirir. Başvuru olmadığı sürece bir **BSTR** ile ayrılan **SysAllocString**, başvuru ile her zaman ayrılır **CoTaskMemAlloc**.  
  
 Her iki dize türü (örneğin, Unicode karakter dizesi gibi) değerine göre sıralanmış olduğunda bir iyileştirme Sıralayıcı Aranan doğrudan bir işaretçi için yeni bir arabellek kopyalamak yerine iç Unicode arabellek yönetilen dizelerde geçirir.  
  
> [!CAUTION]
>  Bir dize değeriyle geçirildiğinde, aranan hiçbir zaman sıralayıcı tarafından geçirilen başvuru değiştirmeniz gerekir. Bunun yapılması, yönetilen yığın bozulmasına neden.  
  
 Zaman bir <xref:System.String?displayProperty=nameWithType> geçirilen başvuruya göre sıralayıcı içeriği dize için ikincil bir arabellek arama yapmadan önce kopyalar. Ardından yeni bir dize çağrısından döndürülen içine arabellek içeriğini kopyalar. Bu teknik değişmez yönetilen dize değiştirilmemiş kalmasını sağlar.  
  
 Zaman bir <xref:System.Text.StringBuilder?displayProperty=nameWithType> değeri, iç arabellek başvuru Sıralayıcı geçişleri tarafından geçirilen **StringBuilder** doğrudan çağırana. Çağıran ve çağrılan arabellek boyutunu kabul etmeniz gerekir. Arayan oluşturmaktan sorumlu bir **StringBuilder** yeterli uzunluğu. Aranan arabellek değil taşması emin olmak için gerekli önlemleri almalıdır. **StringBuilder** olduğu değeri tarafından geçirilen türler başvuru kural için bir özel parametreler olduğu gibi varsayılan olarak geçirilir. Bu her zaman geçirilen olarak giriş/çıkış.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)  
 [Bellek yönetimi ile birlikte çalışma Sıralayıcı](https://msdn.microsoft.com/library/417206ce-ee3e-4619-9529-0c0b686c7bee(v=vs.100))  
 [Tek yönlü öznitelikleri](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [Birlikte Çalışma için Hazırlama](interop-marshaling.md)
