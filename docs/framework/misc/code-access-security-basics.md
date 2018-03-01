---
title: "Kod Erişimi Güvenliği Temelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1fbeae8d01d9ef03c476679ea7fc59273b7a0a0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="code-access-security-basics"></a>Kod Erişimi Güvenliği Temelleri
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Ortak dil çalışma zamanı (diğer bir deyişle, her yönetilen uygulama) hedefleyen her uygulama çalışma zamanı'nın güvenlik sistemi ile etkileşim kurmalıdır. Bir yönetilen uygulamayı yüklendiğinde, konağı bir izin kümesi otomatik olarak verir. Bu izinler, ana bilgisayarın yerel güvenlik ayarları veya bu uygulama korumalı alanı tarafından belirlenir. Bu izinlerine bağlı olarak uygulama düzgün çalışması ya da bir güvenlik özel durumu oluşturur.  
  
 Masaüstü uygulamaları için varsayılan ana bilgisayar tam güvende çalıştırmak için kod sağlar. Uygulamanız Masaüstü hedefliyorsa, bu nedenle, onu bir Kısıtlanmamış izni ayarlayın. Diğer ana bilgisayar veya sanal uygulamalar için sınırlı bir izni sağlar. İznin ana bilgisayardan değiştiğinden, hedef konak sağlayan izinleri kullanmak için uygulamanızı tasarlamanız gerekir.  
  
 Ortak dil çalışma zamanı hedefleyen etkin uygulamaları yazmak için aşağıdaki kod erişim güvenlik kavramları ile bilgi sahibi olmanız gerekir:  
  
-   **Tür kullanımı uyumlu kod**: tür kullanımı uyumlu kod türleri yalnızca iyi tanımlanmış, izin verilen şekillerde erişen kodudur. Örneğin, geçerli nesne başvurusu verilen, tür kullanımı uyumlu kod gerçek alan üyelerine karşılık gelen sabit uzaklıkları bellek erişebilir. Kod rasgele uzaklıkları bellek erişirse o nesnenin genel olarak ait bellek aralığı dışında alanları kullanıma sunulan, tür kullanımı uyumlu değildir. Kod erişim güvenliği yararlanmak kodu etkinleştirmek için doğrulanabilir şekilde tür kullanımı uyumlu kod oluşturur derleyici kullanmanız gerekir. Daha fazla bilgi için bkz: [doğrulanabilir şekilde tür kullanımı uyumlu kod yazma](#typesafe_code) bu konunun ilerleyen bölümlerinde.  
  
-   **Kesinlik temelli ve bildirim temelli söz dizimi**: ortak dil çalışma zamanı hedefleyen kod etkileşim kurabilir güvenlik sistemiyle isteyen izinler tarafından arayanlar izinleri belirttiğiniz yoğun ve belirli güvenlik ayarları (geçersiz kılma yeterli ayrıcalıkları verilir). Program aracılığıyla .NET Framework güvenlik sistemi ile etkileşim kurmak için iki tür sözdizimi kullanın: bildirim temelli söz dizimi ve kesinlik temelli sözdizimi. Bildirim temelli çağrıları özniteliklerini kullanarak gerçekleştirilir; kesinlik temelli çağrıları sınıfları için kodunuzu yeni örneklerini kullanılarak gerçekleştirilir. Bazı çağrıları yalnızca imperatively gerçekleştirilebilir, diğerleri yalnızca bildirimli olarak gerçekleştirilebilir ve bazı çağrıları ya da bir şekilde gerçekleştirilebilir.  
  
-   **Sınıf kitaplıkları güvenli**: kitaplığın arayanlar kitaplığı sunan kaynaklara erişmek için izne sahip olmak için güvenlik taleplerini güvenli sınıf kitaplığı kullanır. Örneğin, bir güvenli sınıf kitaplığı kendi arayanlar dosyaları oluşturmak için izinlere sahip talep dosyaları oluşturmak için bir yöntem olabilir. .NET Framework güvenli sınıf kitaplıkları oluşur. Kodunuzu kullanan herhangi bir kitaplığı erişmek için gerekli izinleri farkında olması gerekir. Daha fazla bilgi için bkz: [güvenli sınıf kitaplıkları kullanarak](#secure_library) bu konunun ilerleyen bölümlerinde.  
  
-   **Saydam kod**: başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], özel izinler tanımlayan ek olarak, ayrıca kodunuzu olarak güvenlik saydam çalıştırılması gerekip gerekmediğini belirlemeniz gerekir. Güvenliği saydam kod türleri veya tanımlanır üyeleri olarak güvenlik kritik çağrılamaz. Bu kural, kısmen güvenilir uygulamalar yanı sıra tam güven uygulamaları için geçerlidir. Daha fazla bilgi için bkz: [güvenliği saydam kod](../../../docs/framework/misc/security-transparent-code.md).  
  
<a name="typesafe_code"></a>   
## <a name="writing-verifiably-type-safe-code"></a>Doğrulanabilir şekilde tür kullanımı uyumlu kod yazma  
 Tam zamanında (JIT) derleme kodunu inceler ve kodun tür kullanımı uyumlu olup olmadığını belirlemek çalışır bir doğrulama işlemi gerçekleştirir. Tür kullanımı uyumlu olması için doğrulama sırasında kanıtlanmış kod çağrılır *doğrulanabilir şekilde tür kullanımı uyumlu kod*. Kodu tür kullanımı uyumlu olabilir, henüz sınırlamalar doğrulama işlemi veya derleme nedeniyle doğrulanabilir şekilde tür kullanımı uyumlu olmayabilir. Tür kullanımı uyumlu olmayan tüm diller ve Microsoft Visual C++ gibi bazı dil derleyicileri doğrulanabilir şekilde tür kullanımı uyumlu yönetilen kod oluşturulamıyor. Kullandığınız dil derleyici doğrulanabilir şekilde tür kullanımı uyumlu kod oluşturur olup olmadığını belirlemek için derleyicinin belgelerine başvurun. Bazı dil yapıları kaçının yalnızca yükleyen doğrulanabilir şekilde tür kullanımı uyumlu kod oluşturur bir dil derleyici kullanırsanız kullanmak isteyebileceği [PEVerify aracı](../../../docs/framework/tools/peverify-exe-peverify-tool.md) kodunuzu doğrulanabilir şekilde tür kullanımı uyumlu olup olmadığını belirlemek için.  
  
 Doğrulanabilir şekilde tür kullanımı uyumlu olmayan kodu güvenlik ilkesini doğrulama atlamak kod sağlar, yürütmeyi deneyebilirsiniz. Ancak, tür güvenliği zamanının mekanizmasının yalıtmak derlemeler için önemli bir parçası olduğundan, kod tür güvenliği kuralları bozup güvenlik güvenilir bir şekilde uygulanamaz. Varsayılan olarak, yalnızca yerel bilgisayardan geliyorsa çalıştırmak için tür kullanımı uyumlu olmayan kodu izin verilir. Bu nedenle, mobil kod tür kullanımı uyumlu olmalıdır.  
  
<a name="secure_library"></a>   
## <a name="using-secure-class-libraries"></a>Güvenli sınıf kitaplıkları kullanma  
 Kodunuzu ister ve ise sınıf kitaplığı tarafından gerekli izinlerin, kitaplık erişimine izin verilmez ve kitaplık sunar kaynaklarını yetkisiz erişimden korunur. Kodunuzu uygun izinlere sahip değilse bu sınıf kitaplığı erişmesine izin verilmez ve kötü amaçlı kod dolaylı olarak korunan kaynaklara erişim için kodunuzu kullanmanız mümkün olmayacaktır. Kodunuzu çağırması başka bir kod kitaplığı erişim izni de olmalıdır. Yoksa, kodunuzu da çalışıyor sınırlı.  
  
 Kod erişimi güvenliği, kod yazma İnsan hatası olasılığını ortadan kaldırmaz. Uygulamanız, korunan kaynaklara erişim için güvenli sınıf kitaplıkları kullanıyorsa, sınıf kitaplıkları yakından olası güvenlik sorunlarını scrutinized çünkü ancak, uygulama kodu için güvenlik riski, azalır.  
  
## <a name="declarative-security"></a>Bildirim Temelli Güvenlik  
 Bildirim temelli güvenlik söz dizimini kullanır [öznitelikleri](../../../docs/standard/attributes/index.md) güvenlik bilgileri yerleştirmek için [meta veri](../../../docs/standard/metadata-and-self-describing-components.md) kodunuzun. İstek, isteğe bağlı veya kullanmak istediğiniz geçersiz kılma türünü belirtmek için derleme, sınıf veya üye düzeyinde öznitelikleri yerleştirilebilir. İstekleri çalışma zamanı güvenlik sistemi uygulamanız gerekir veya istemediğinizi izinleri hakkında bilgilendirmek için ortak dil çalışma zamanı hedef uygulamalarda kullanılır. Taleplerin ve geçersiz kılmalar kitaplıklarında arayanlar kaynakların korunmasına yardımcı olmak için veya varsayılan güvenlik davranışını geçersiz kılmak için kullanılır.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], terminolojisi ve .NET Framework güvenlik modelinin önemli değişiklikler olmuştur. Bu değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Bildirim temelli güvenlik çağrıları kullanabilmeniz için böylece izni gereksinim duyduğunuz belirli formu temsil eden izni nesne durumu verileri başlatması gerekir. Geçirilen bir öznitelik her yerleşik iznine sahip bir <xref:System.Security.Permissions.SecurityAction> uygulamak istediğiniz güvenlik işlemi türünü tanımlamak için numaralandırması. Ancak, izinleri de onlara özel kendi parametreleri kabul eder.  
  
 Aşağıdaki kod parçası, kodun arayanlar adlı özel bir izne sahip isteyen bildirim temelli söz dizimini gösterir `MyPermission`. Bu izni kuramsal özel izinleri ve .NET Framework mevcut değil. Bu örnekte, bu izin için sınıf düzeyinde uygulanacağını belirtme doğrudan sınıf tanımını önce bildirim temelli çağrısı yerleştirilir. Öznitelik geçirilen bir **SecurityAction.Demand** yapısı belirtin arayanlar çalıştırmak için bu izni olmalıdır.  
  
```vb  
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1  
  
   Public Sub New()  
      'The constructor is protected by the security call.  
   End Sub  
  
   Public Sub MyMethod()  
      'This method is protected by the security call.  
   End Sub  
  
   Public Sub YourMethod()  
      'This method is protected by the security call.  
   End Sub  
End Class  
```  
  
```csharp  
[MyPermission(SecurityAction.Demand, Unrestricted = true)]  
public class MyClass  
{  
   public MyClass()  
   {  
      //The constructor is protected by the security call.  
   }  
  
   public void MyMethod()  
   {  
      //This method is protected by the security call.  
   }  
  
   public void YourMethod()  
   {  
      //This method is protected by the security call.  
   }  
}  
```  
  
## <a name="imperative-security"></a>Kesin Temelli Güvenlik  
 Kesinlik temelli güvenliği sözdizimi çağırma izni nesne yeni bir örneğini oluşturarak güvenlik çağrısı verir. Kesinlik temelli sözdizimi, talepleri ve geçersiz kılmalar, ancak değil isteklerini gerçekleştirmek için kullanabilirsiniz.  
  
 Çağrı güvenliği yapmadan önce böylece ihtiyacınız izni belirli formu temsil eden izni nesne durumu verileri başlatması gerekir. Örneğin, oluşturulurken bir <xref:System.Security.Permissions.FileIOPermission> Nesne oluşturucusu başlatmak için kullanabileceğiniz **FileIOPermission** böylece tüm dosyalar ya da dosyalara erişimi yok ya da Kısıtlanmamış erişim gösteren nesne. Ya da farklı bir kullanabilirsiniz **FileIOPermission** (diğer bir deyişle, okuma, ekleme veya yazma) temsil eder ve dosyaları korumak için nesne istediğiniz için istediğiniz erişim türünü belirten parametreleri nesne geçirme nesnesi.  
  
 Tek güvenlik nesnesi çağrılacak kesinlik temelli güvenliği sözdizimini kullanarak ek olarak, bir izin kümesi izinler grubudur başlatmak için kullanabilirsiniz. Örneğin, bu teknik güvenilir bir şekilde gerçekleştirmek için tek yoludur [assert](../../../docs/framework/misc/using-the-assert-method.md) birden çok izinleri bir yöntemi çağırır. Kullanım <xref:System.Security.PermissionSet> ve <xref:System.Security.NamedPermissionSet> sınıfları izinleri bir grup oluşturun ve sonra istenen güvenlik çağrısı başlatılacak uygun yöntemini çağırın.  
  
 Kesinlik temelli sözdizimi, talepleri ve geçersiz kılmalar, ancak değil isteklerini gerçekleştirmek için kullanabilirsiniz. Kesinlik temelli sözdizimi için taleplerini kullanabilir ve izin durumu başlatmak için gereken bilgileri yalnızca çalışma zamanında bilinen duruma etkinleştirildiğinde yerine tanımlayıcı sözdizimi geçersiz kılar. Örneğin, arayanlar belirli bir dosyayı okuma izni vardır, ancak çalışma zamanına kadar bu dosya adını bilmiyorsanız emin olmak istiyorsanız, kesinlik temelli bir isteğe bağlı kullanın. Ayrıca çalışma zamanında bir koşul tutan olup olmadığını belirlemek gerektiğinde kesinlik temelli denetimleri yerine bildirim temelli denetimleri kullanın ve test sonuçlarına dayalı bir güvenlik isteğe bağlı yapmak (veya değil) tercih.  
  
 Aşağıdaki kod parçası, kodun arayanlar adlı özel bir izne sahip isteyen kesinlik temelli söz dizimini gösterir `MyPermission`. Bu izni kuramsal özel izinleri ve .NET Framework mevcut değil. Yeni bir örneğini `MyPermision` oluşturulan `MyMethod`, bu yöntem yalnızca güvenlik çağrısı ile kullanılan koruyarak.  
  
```vb  
Public Class MyClass1  
  
   Public Sub New()  
  
   End Sub  
  
   Public Sub MyMethod()  
      'MyPermission is demanded using imperative syntax.  
      Dim Perm As New MyPermission()  
      Perm.Demand()  
      'This method is protected by the security call.  
   End Sub  
  
   Public Sub YourMethod()  
      'YourMethod 'This method is not protected by the security call.  
   End Sub  
End Class  
```  
  
```csharp  
public class MyClass {  
   public MyClass(){  
  
   }  
  
   public void MyMethod() {  
       //MyPermission is demanded using imperative syntax.  
       MyPermission Perm = new MyPermission();  
       Perm.Demand();  
       //This method is protected by the security call.  
   }  
  
   public void YourMethod() {  
       //This method is not protected by the security call.  
   }  
}  
```  
  
## <a name="using-managed-wrapper-classes"></a>Yönetilen Sarmalayıcı Sınıflarını Kullanma  
 Çoğu uygulamaları ve bileşenleri (dışında güvenli kitaplıklar) doğrudan yönetilmeyen kod çağırmalıdır değil. Bunun birkaç nedeni vardır. Kod yönetilmeyen kod doğrudan çağırırsa, onu yerel kod çağırmak için güven yüksek düzeyde kod verilmesi gerekir çünkü çoğu durumda çalıştırmak için verilmez. İlke, bu tür bir uygulamanın çalışmasına izin vermek için değiştirilirse, önemli ölçüde uygulama neredeyse her işlemi gerçekleştirmek boş bırakın, sistem güvenliğini zayıflatabilir.  
  
 Ayrıca, yönetilmeyen kod erişmek için izne sahip code yönetilmeyen API çağırarak büyük olasılıkla neredeyse her işlemi gerçekleştirebilir. Örneğin, yönetilmeyen kodu çağırma izni olan kod ihtiyaç duymadığı <xref:System.Security.Permissions.FileIOPermission> ; bir dosyaya erişmek için yalnızca bir yönetilmeyen (Win32) dosya API'si yönetilen dosya gerektirir API'si atlayarak doğrudan çağırabilir **FileIOPermission**. Yönetilen kod yönetilmeyen kodu çağırma izni varsa ve doğrudan yönetilmeyen koda çağrı, çalışma zamanı tür kısıtlamaları yönetilmeyen kod zorlayamaz beri güvenlik kısıtlamaları, güvenilir bir şekilde zorlamak güvenlik sistemi yükleyemez.  
  
 Yönetilmeyen kod erişim gerektiren bir işlem gerçekleştirmek için uygulamanızın istiyorsanız, bunu gerekli işlevselliği (böyle bir sınıf varsa) kaydırılan güvenilen bir yönetilen sınıf ile yapmalısınız. Güvenli Sınıf Kitaplığı'nda zaten varsa bir sarmalayıcı sınıfı kendiniz oluşturmayın. Yönetilmeyen koda çağrı yapmak için izin verilmesi için güven yüksek derecede verilmelidir, sarmalayıcı sınıfı, kendi arayanlar uygun izinlere sahip yoğun sorumludur. Sarmalayıcı sınıfı kullanırsanız, kodunuzu yalnızca istek ve sarmalayıcı sınıfı için gereken izinlere sahip gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.NamedPermissionSet>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Assert](../../../docs/framework/misc/using-the-assert-method.md)  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)  
 [Kod erişim güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)  
 [Öznitelikler](../../../docs/standard/attributes/index.md)  
 [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)
