---
title: Kod Erişim Güvenliği Temelleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d5a5658fcb6bbba72938a16a9e5c82fd779e2e3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352964"
---
# <a name="code-access-security-basics"></a>Kod Erişim Güvenliği Temelleri

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Ortak dil çalışma zamanı (diğer bir deyişle, her yönetilen uygulamanın) hedefleyen her uygulama, çalışma zamanının güvenlik sistemi ile etkileşim gerekir. Bir yönetilen uygulamayı yüklendiğinde, ana bilgisayar bir izin kümesi otomatik olarak verir. Bu izinler, uygulamanın bulunduğu bir korumalı alan veya ana bilgisayarın yerel güvenlik ayarları tarafından belirlenir. Bu izinlere bağlı olarak uygulama düzgün çalışmasına veya bir güvenlik özel durumu oluşturur.

Masaüstü uygulamaları için varsayılan ana bilgisayar tam güvende çalıştırmak için kod sağlar. Masaüstü uygulamanızın olmasını istiyorsanız, bu nedenle, bunu bir Kısıtlanmamış izni ayarlayın. Diğer konaklar veya sanal uygulamaları için sınırlı bir izni sağlar. İzin kümesi ana bilgisayardan diğerine değişebileceği için uygulamanızı hedef ana sağlayan izinleri kullanacak şekilde tasarlamanız gerekir.

Ortak dil çalışma zamanını hedefleyen etkili uygulamalar yazmak üzere aşağıdaki kod erişim güvenlik kavramlarına alışık olmanız gerekir:

- **Tür kullanımı uyumlu kod**: Tür kullanımı uyumlu kod türleri yalnızca iyi tanımlanmış, izin verilen şekilde erişen kodudur. Örneğin, geçerli nesne başvurusu göz önünde bulundurulduğunda, tür kullanımı uyumlu kod karşılık gelen gerçek alan üyelerine sabit uzaklıkları bellek erişebilirsiniz. Kod rastgele uzaklıkları bellek erişirse, o nesnenin genel olarak ait bellek aralığının dışında alanları kullanıma sunulan, tür kullanımı uyumlu değil. Kod erişim güvenlik kodu etkinleştirmek için doğrulanabilir şekilde tür kullanımı uyumlu kod oluşturur bir derleyici kullanmanız gerekir. Daha fazla bilgi için [doğrulanabilir şekilde tür kullanımı uyumlu kod yazma](#typesafe_code) bu konunun ilerleyen bölümlerinde.

- **Kesinlik temelli ve bildirim temelli söz dizimi**: Çağıranlar izinleri belirttiğiniz yoğun ve (yeterli ayrıcalıklar verilir) bazı güvenlik ayarlarını geçersiz kılma izinler isteyen tarafından ortak dil çalışma zamanı güvenlik sistemi ile etkileşim kurabilir hedefleyen kod. Program aracılığıyla .NET Framework güvenlik sistemini ile etkileşim kurmak için iki sözdizimi biçimi kullanın: bildirim temelli söz dizimi ve kesinlik temelli sözdizimi. Bildirim temelli çağrı, öznitelikleri kullanarak gerçekleştirilir; kesinlik temelli çağrı, yeni kod içindeki sınıf örnekleri kullanılarak gerçekleştirilir. Bazı çağrıları yalnızca kesin gerçekleştirilebilir, diğerleri yalnızca bildirimli olarak gerçekleştirilebilir ve bazı çağrıları her iki şekilde gerçekleştirilebilir.

- **Güvenli sınıf kitaplıkları**: Güvenli sınıf kitaplığı, kitaplık çağıranlar kitaplığı kullanan kaynaklara erişim izni sağlamak için güvenlik taleplerini kullanır. Örneğin, bir güvenli sınıf kitaplığı çağıranlarını dosyaları oluşturmak için izinlere sahip isteğe bağlı dosyaları oluşturmak için bir yöntem olabilir. Güvenli sınıf kitaplıkları .NET Framework oluşur. Kodunuzun kullandığı herhangi bir kitaplığı erişmek için gerekli izinleri farkında olması gerekir. Daha fazla bilgi için [güvenli sınıf kitaplıkları kullanarak](#secure_library) bu konunun ilerleyen bölümlerinde.

- **Saydam kod**: İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], özel izinler belirlemeye ek olarak, ayrıca kodunuz gibi güvenlik saydam çalıştırılması gerekip gerekmediğini belirlemeniz gerekir. Güvenliği saydam kod türleri veya üyeleri tanımlanmış olarak güvenlik kritik çağrılamıyor. Bu kural, kısmen güvenilir uygulamaların yanı sıra tam güven uygulamaları için geçerlidir. Daha fazla bilgi için [güvenliği saydam kod](../../../docs/framework/misc/security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Doğrulanabilir şekilde tür kullanımı uyumlu kod yazma

Just-in-time (JIT) derleme kodu inceler ve kod tür kullanımı uyumlu olup olmadığını belirlemeye çalışır bir doğrulama işlemi gerçekleştirir. Tür kullanımı uyumlu olacak şekilde, doğrulama sırasında kanıtlanmış bir kodu çağrılır *doğrulanabilir şekilde tür kullanımı uyumlu kod*. Kod tür kullanımı uyumlu olabilir, henüz sınırlamaları doğrulama işlemi veya derleme nedeniyle doğrulanabilir şekilde tür kullanımı uyumlu olmayabilir. Tür kullanımı uyumlu tüm dillerde ve Microsoft Visual C++ gibi bazı dil derleyicileri doğrulanabilir şekilde tür kullanımı uyumlu yönetilen kod üretilemiyor. Kullandığınız dil derleyicisi doğrulanabilir şekilde tür kullanımı uyumlu kod üretir olup olmadığını belirlemek için derleyicinin belgelerine bakın. Yalnızca belirli dil yapılarını kaçınırsınız yükleyen doğrulanabilir şekilde tür kullanımı uyumlu kod oluşturur bir dil derleyicisi kullanıyorsanız kullanmak isteyebilirsiniz [PEVerify aracı](../../../docs/framework/tools/peverify-exe-peverify-tool.md) kodunuzu doğrulanabilir şekilde tür kullanımı uyumlu olup olmadığını belirlemek için.

Doğrulanabilir şekilde tür kullanımı uyumlu olmayan kodu doğrulamasını atlamak kodun güvenlik ilkesi izin veriyorsa yürütülecek deneyebilirsiniz. Ancak, tür güvenliği yalıtmak derlemeleri için çalışma zamanının mekanizması önemli bir parçası olduğundan, kod tür güvenliği kurallarını ihlal ediyorsa güvenlik güvenilir bir şekilde zorlanamaz. Varsayılan olarak, yalnızca yerel bilgisayardan geliyorsa çalıştırmak için tür açısından güvenli olmayan kodu izin verilir. Bu nedenle, mobil kod tür kullanımı uyumlu olmalıdır.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Güvenli sınıf kitaplıklarını kullanma

Kodunuz ister ve sınıf kitaplığının gerekli izinlerin, kitaplığınıza erişmesine izin verilir ve kitaplık sunan kaynakların yetkisiz erişime karşı korunur. Kodunuzu uygun izinlere sahip değilse, sınıf kitaplığınıza erişmesine izin verilmez ve kötü amaçlı kod dolaylı olarak korunan kaynaklara erişim için kodunuzu kullanmanız mümkün olmayacaktır. Kodunuzu çağıran başka bir kod kitaplığı erişim izni de olmalıdır. Kullanmıyorsa, kodunuzu da çalışıyor sınırlanır.

Kod erişimi güvenliği, kod yazma İnsan hatası olasılığını ortadan kaldırmaz. Uygulamanız, korunan kaynaklara erişim için güvenli sınıf kitaplıkları kullanıyorsa, sınıf kitaplıkları yakından için olası güvenlik sorunlarını scrutinized çünkü ancak uygulama kodu için güvenlik riski, azalır.

## <a name="declarative-security"></a>Bildirim Temelli Güvenlik

Bildirim temelli güvenlik sözdizimi kullanan [öznitelikleri](../../../docs/standard/attributes/index.md) güvenlik bilgileri yerleştirmek için [meta verileri](../../../docs/standard/metadata-and-self-describing-components.md) kodunuzun. İstek, isteğe bağlı veya kullanmak istediğiniz geçersiz kılma türünü belirtmek için derleme, sınıf veya üye düzeyinde öznitelikler yerleştirilebilir. İstekleri, çalışma zamanı güvenlik sistemi uygulamanız gereken veya istediğiniz izinleri hakkında bilgilendirmek için ortak dil çalışma zamanını hedefleyen uygulamalarda kullanılır. Talepleri ve geçersiz kılmalar kitaplıklarında çağrı yapanlardan kaynaklarını korumak için veya varsayılan güvenlik davranışı geçersiz kılmak için kullanılır.

> [!NOTE]
> İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], terminolojisi ve .NET Framework güvenlik modelinin önemli değişiklikler olmuştur. Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).

Bildirim temelli güvenlik çağrıları kullanmak için izne ihtiyacınız belirli şeklinde gösterir böylece izni nesne durumu verilerini başlatmanız gerekir. Geçirilen bir öznitelik her yerleşik izni bir <xref:System.Security.Permissions.SecurityAction> uygulamak istediğiniz güvenlik işleminin türünü açıklayan sabit listesi. Ancak, izinleri de bunları dışlar kendi parametreleri kabul eder.

Aşağıdaki kod parçası kodunuzun çağıranlar adlı bir özel izni olduğunu istemeye ilişkin bildirim temelli söz dizimi görülmektedir `MyPermission`. Bu izin, kuramsal bir özel izni ve .NET Framework'teki yok. Bu örnekte, bildirim temelli çağrı, doğrudan sınıf tanımı, bu izin için sınıf düzeyinde uygulanacağını belirleme önce yerleştirilir. Öznitelik geçirilen bir **SecurityAction.Demand** çağıranlar çalıştırmak için bu izne sahip olması gerektiğini belirtmenize yapısı.

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

Kesinlik temelli güvenlik sözdizimi, çağırmak istediğiniz izin nesnesi yeni bir örneğini oluşturarak güvenlik çağrısı verir. Kesinlik temelli sözdizimi, talepleri ve geçersiz kılmalar, ancak değil isteklerini gerçekleştirmek için kullanabilirsiniz.

Güvenlik çağrı yapmadan önce böylece belirli formun ihtiyacınız iznin temsil ettiği izni nesne durumu verilerini başlatmanız gerekir. Örneğin, oluşturulurken bir <xref:System.Security.Permissions.FileIOPermission> nesnesini başlatmak için oluşturucu kullanabilirsiniz **FileIOPermission** böylece tüm dosyalara veya dosyaları erişim yok ya da sınırsız erişim gösteren nesne. Ya da farklı bir kullanabilirsiniz **FileIOPermission** (diğer bir deyişle, okuma, ekleme veya yazma) temsil eder ve dosyaları korumak için nesne istediğiniz nesneyi istediğiniz erişim türünü belirten parametreleri geçirme nesnesi.

Kesinlik temelli güvenlik sözdizimi tek güvenlik nesnesi çağırmak için kullanmanın yanı sıra, bir grup bir izin kümesindeki izinlerin başlatmak için kullanabilirsiniz. Örneğin, bu tekniği güvenilir bir şekilde gerçekleştirmek için tek yoludur [assert](../../../docs/framework/misc/using-the-assert-method.md) birden fazla izinleri bir yöntemi çağırır. Kullanım <xref:System.Security.PermissionSet> ve <xref:System.Security.NamedPermissionSet> izinlerine oluşturun ve ardından istenen güvenlik arama çağırmak için uygun yöntem çağırmak için sınıflar.

Kesinlik temelli sözdizimi, talepleri ve geçersiz kılmalar, ancak değil isteklerini gerçekleştirmek için kullanabilirsiniz. Kesinlik temelli sözdizimi talepleri için kullanabilir ve izin durumu başlatmak için gereken bilgileri yalnızca çalışma zamanında bildiği etkinleştirildiğinde yerine bildirim temelli söz dizimi geçersiz kılar. Örneğin, Arayanların belirli bir dosyayı okuma izniniz yok, ancak çalışma zamanına kadar bu dosyanın adını bilmiyorsanız emin olmak istiyorsanız, kesinlik temelli bir isteğe bağlı kullanın. Ayrıca, çalışma zamanında koşul tutan olup olmadığını belirlemek gerektiğinde kesinlik temelli denetimleri yerine bildirim temelli denetimlerini kullanın ve test sonucuna göre bir güvenlik talebi yapmak (veya etkinleştirmezsiniz) tercih.

Aşağıdaki kod parçası isteyen kodunuzun çağıranlar adlı bir özel izni olduğunu kesinlik temelli sözdizimi gösterilmektedir `MyPermission`. Bu izin, kuramsal bir özel izni ve .NET Framework'teki yok. Yeni bir örneğini `MyPermission` oluşturulur `MyMethod`, bu yöntem yalnızca güvenlik çağrısı ile kullanılan koruyarak.

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

Çoğu uygulamaları ve bileşenleri (dışında güvenli kitaplıklar) doğrudan yönetilmeyen kod çağırmamanız gerekir. Bunun birkaç nedeni vardır. Kod yönetilmeyen kodu doğrudan çağırırsa, bu kod yüksek düzeyde yerel kod çağırmak için güven verilmesi gerekir çünkü birçok durumda çalıştırılacak verilmez. İlke, bu tür bir uygulama çalıştırmasına izin verecek şekilde değiştirilirse, önemli ölçüde neredeyse tüm işlemi gerçekleştirmek ücretsiz uygulama bırakarak sistemin güvenlik zayıflatabilir.

Ayrıca, yönetilmeyen koda erişim iznine sahip kodu yönetilmeyen API çağırarak büyük olasılıkla neredeyse tüm işlemi gerçekleştirebilir. Örneğin, yönetilmeyen kod çağırmak için izni olan kod ihtiyaç duymadığı <xref:System.Security.Permissions.FileIOPermission> bir dosyaya erişmek için yalnızca bir yönetilmeyen (Win32) dosya API'si yönetilen dosya API'SİNİN atlayarak doğrudan çağırabilir **FileIOPermission**. Yönetilen kodun yönetilmeyen koda çağrı izni olan ve doğrudan yönetilmeyen koda çağrı, güvenlik sistem çalışma zamanı yönetilmeyen kod tür kısıtlamaları zorunlu kılamaz beri güvenlik kısıtlamaları, güvenilir bir şekilde uygulamak mümkün olmayacaktır.

Yönetilmeyen kod erişim gerektiren bir işlem gerçekleştirmek için uygulamanızı isterseniz, bunu (böyle bir sınıfı varsa) gerekli işlevselliği sarmalayan güvenilen bir yönetilen sınıf ile yapmalısınız. Güvenli sınıf kitaplığında zaten varsa, bir sarmalayıcı sınıfı kendiniz oluşturmayın. Yüksek derecede güven yönetilmeyen koda çağrı yapmak için izin verilmesi gerekir, sarmalayıcı sınıfı çağıranlarını uygun izinlere sahip zorlu için sorumludur. Sarmalayıcı sınıfı kullanırsanız, kodunuzun yalnızca istek ve sarmalayıcı sınıfı talepleri izinlerinin verilmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](../../../docs/framework/misc/using-the-assert-method.md)
- [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
- [Kod erişimi güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)
- [Öznitelikler](../../../docs/standard/attributes/index.md)
- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)
