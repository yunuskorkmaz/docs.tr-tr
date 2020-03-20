---
title: Kod Erişim Güvenliği Temelleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
ms.openlocfilehash: 08d708e8f98bd2fe06757df3033a512e2fe1f3c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400059"
---
# <a name="code-access-security-basics"></a>Kod Erişim Güvenliği Temelleri

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Ortak dil çalışma süresini (diğer bir şekilde yönetilen her uygulama) hedefleyen her uygulama, çalışma zamanının güvenlik sistemiyle etkileşime girmelidir. Yönetilen bir uygulama yüklendiğinde, ana bilgisayar otomatik olarak bir dizi izin verir. Bu izinler, ana bilgisayar yerel güvenlik ayarlarıveya uygulamanın içinde olduğu kum havuzu tarafından belirlenir. Bu izinlere bağlı olarak, uygulama düzgün çalışır veya bir güvenlik özel durumu oluşturur.

Masaüstü uygulamaları için varsayılan ana bilgisayar kodun tam güven içinde çalışmasını sağlar. Bu nedenle, uygulamanız masaüstü hedefliyorsa, sınırsız bir izin kümesi vardır. Diğer ana bilgisayarlar veya zAndA Kutuları, uygulamalar için sınırlı bir izin kümesi sağlar. İzin kümesi ana bilgisayardan ana bilgisayara değişebildiği için, uygulamanızı yalnızca hedef ana bilgisayarınızın izin verdiği izinleri kullanacak şekilde tasarlamanız gerekir.

Ortak dil çalışma süresini hedefleyen etkili uygulamalar yazmak için aşağıdaki kod erişim güvenlik kavramlarına aşina olmalısınız:

- **Tür-güvenli kod**: Tür-güvenli kod, yalnızca iyi tanımlanmış, izin verilebilen yollarla türlere erişen koddur. Örneğin, geçerli bir nesne başvurusu verilen tür-güvenli kod, gerçek alan üyelerine karşılık gelen sabit uzaklıklarda belleğe erişebilir. Kod, söz konusu nesnenin genel olarak açıkta kalan alanlarına ait bellek aralığı dışında rasgele uzaklıklarda belleğe erişiyorsa, tür güvenli değildir. Kodun kod erişim güvenliğinden yararlanmasını sağlamak için, doğrulanabilir şekilde tür desafe kodu üreten bir derleyici kullanmanız gerekir. Daha fazla bilgi için, bu konunun ilerleyen bölümlerinde [Doğrulanabilir Tür-Güvenli Kod Yazma](#typesafe_code) bölümüne bakın.

- **Zorunlu ve bildirimsel sözdizimi**: Ortak dil çalışma zamanını hedefleyen kod, izin ler isteyerek, arayanların belirli izinlere sahip olduğunu talep ederek ve belirli güvenlik ayarlarını geçersiz kılarak (yeterli ayrıcalık lar verilir) güvenlik sistemiyle etkileşim kurabilir. .NET Framework güvenlik sistemiyle programlı olarak etkileşimde kalmak için iki sözdizimi biçimi kullanırsınız: bildirimsel sözdizimi ve zorunlu sözdizimi. Bildirimsel çağrılar öznitelikler kullanılarak gerçekleştirilir; zorunlu çağrılar, kodunuzdaki yeni sınıf örnekleri kullanılarak gerçekleştirilir. Bazı aramalar yalnızca zorunlu olarak gerçekleştirilebilir, diğerleri yalnızca bildirimsel olarak gerçekleştirilebilir ve bazı çağrılar her iki şekilde de gerçekleştirilebilir.

- **Güvenli sınıf kitaplıkları**: Güvenli sınıf kitaplığı, kitaplığın arayanların kitaplığın açığa çıkardığı kaynaklara erişmek için izin sahibi olmasını sağlamak için güvenlik taleplerini kullanır. Örneğin, güvenli bir sınıf kitaplığı, arayanların dosya oluşturma izinlerine sahip olmasını gerektiren dosyalar oluşturmak için bir yönteme sahip olabilir. .NET Framework güvenli sınıf kitaplıklarından oluşur. Kodunuzun kullandığı kitaplıklara erişmek için gereken izinlerden haberdar olmalısınız. Daha fazla bilgi için, bu konuda daha sonra [Güvenli Sınıf Kitaplıkları Kullanma](#secure_library) bölümüne bakın.

- **Saydam kod**: .NET Framework 4'ten başlayarak, belirli izinleri tanımlamaya ek olarak, kodunuzu güvenlik saydamı olarak çalıştırıp çalıştırmamanız gerektiğini de belirlemeniz gerekir. Güvenlik saydam kodu, güvenlik açısından kritik öneme sahip olarak tanımlanan türleri veya üyeleri arayamaz. Bu kural, tam güven uygulamalarının yanı sıra kısmen güvenilen uygulamalar için de geçerlidir. Daha fazla bilgi için [Güvenlik Saydam Kodu'na](security-transparent-code.md)bakın.

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Doğrulanabilir Tür-Güvenli Kod Yazma

Tam zamanında (JIT) derleme, kodu inceleyen ve kodun tür açısından güvenli olup olmadığını belirlemeye çalışan bir doğrulama işlemi gerçekleştirir. Doğrulama sırasında tür güvenli olduğu kanıtlanmış *koda doğrulanabilir tür-güvenli kod*denir. Kod tür açısından güvenli olabilir, ancak doğrulama işleminin veya derleyicinin sınırlamaları nedeniyle doğrulanabilir şekilde tür güvenli olmayabilir. Tüm diller tür güvenli değildir ve Microsoft Visual C++gibi bazı dil derleyicileri doğrulanabilir şekilde tür de güvenli yönetilen kod oluşturamaz. Kullandığınız dil derleyicisinin doğrulanabilir türde güvenli kod oluşturup oluşturmadığını belirlemek için derleyicinin belgelerine başvurun. Yalnızca belirli dil yapılarından kaçındığınızda doğrulanabilir şekilde türde güvenli kod oluşturan bir dil derleyicisi kullanıyorsanız, kodunuzu doğrulanabilir şekilde tür de güvenli olup olmadığını belirlemek için [PEVerify aracını](../tools/peverify-exe-peverify-tool.md) kullanmak isteyebilirsiniz.

Doğrulanabilir tür güvenli olmayan kod, güvenlik ilkesi kodun doğrulamayı atlamasına izin veriyorsa yürütmeyi deneyebilir. Ancak, tür güvenliği derlemeleri yalıtma için çalışma zamanı mekanizmasının önemli bir parçası olduğundan, kod tür güvenliği kurallarını ihlal ederse güvenlik güvenilir bir şekilde uygulanamaz. Varsayılan olarak, tür güvenli olmayan kodun yalnızca yerel bilgisayardan kaynaklanıyorsa çalışmasına izin verilir. Bu nedenle, mobil kod tür güvenli olmalıdır.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Güvenli Sınıf Kitaplıklarını Kullanma

Kodunuz sınıf kitaplığı tarafından gerekli izinleri isterse ve izinler verilirse, kitaplık ve kitaplığın açığa çıkardığı kaynaklara yetkisiz erişime karşı korunur. Kodunuz uygun izinlere sahip değilse, sınıf kitaplığına erişmesine izin verilmez ve kötü amaçlı kod, korumalı kaynaklara dolaylı olarak erişmek için kodunuzu kullanamaz. Kodunuzu çağıran diğer kodların da kitaplıklara erişim izni olmalıdır. Yoksa, kodunuz da çalıştırılacak şekilde kısıtlanır.

Kod erişim güvenliği kod yazarken insan hatası olasılığını ortadan kaldırmaz. Ancak, uygulamanız korumalı kaynaklara erişmek için güvenli sınıf kitaplıkları kullanıyorsa, sınıf kitaplıkları olası güvenlik sorunlarına karşı yakından incelendiği için uygulama kodu için güvenlik riski azalır.

## <a name="declarative-security"></a>Bildirim Temelli Güvenlik

Bildirimsel güvenlik sözdizimi, güvenlik bilgilerini kodunuzu [meta verilerine](../../standard/metadata-and-self-describing-components.md) yerleştirmek için [öznitelikleri](../../standard/attributes/index.md) kullanır. Öznitelikler, kullanmak istediğiniz istek, talep veya geçersiz kılma türünü belirtmek için derlemeye, sınıfa veya üye düzeye yerleştirilebilir. İstekler, çalışma zamanı güvenlik sistemini uygulamanızın ihtiyaç duyduğu veya istemediği izinler hakkında bilgilendirmek için ortak dil çalışma süresini hedefleyen uygulamalarda kullanılır. Talepler ve geçersiz kılmalar, kaynakları arayanlardan korumaya yardımcı olmak veya varsayılan güvenlik davranışını geçersiz kılmak için kitaplıklarda kullanılır.

> [!NOTE]
> .NET Framework 4'te .NET Framework güvenlik modeli nde ve terminolojisinde önemli değişiklikler olmuştur. Bu değişiklikler hakkında daha fazla bilgi için [Güvenlik Değişiklikleri'ne](../security/security-changes.md)bakın.

Bildirimsel güvenlik çağrılarını kullanmak için, gereksinim duyduğunuz belirli izin biçimini temsil etmesi için izin nesnesinin durum verilerini başlatmanız gerekir. Her yerleşik izin, gerçekleştirmek istediğiniz güvenlik <xref:System.Security.Permissions.SecurityAction> işlemi türünü açıklamak için numaralandırmadan geçirilen bir özniteliğe sahiptir. Ancak, izinler kendilerine özel olan kendi parametrelerini de kabul eder.

Aşağıdaki kod parçası, kodunuzu arayanların özel bir izin ekiolarak `MyPermission`talep etmek için bildirimsel sözdizimini gösterir. Bu izin varsayımsal bir özel izindir ve .NET Framework'de bulunmaz. Bu örnekte, bildirimçağrısı sınıf tanımının hemen önüne yerleştirilir ve bu iznin sınıf düzeyine uygulanacağı belirtilir. Öznitelik, arayanların çalıştırmak için bu izne sahip olması gerektiğini belirtmek için bir **SecurityAction.Demand** yapısından geçirilir.

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

Zorunlu güvenlik sözdizimi, çağırmak istediğiniz izin nesnesinin yeni bir örneğini oluşturarak bir güvenlik çağrısı verir. Talepleri gerçekleştirmek ve geçersiz kılabilir, ancak istekleri geçersiz kılmak için zorunlu sözdizimini kullanabilirsiniz.

Güvenlik aramasını yapmadan önce, gereksinim duyduğunuz iznin belirli biçimini temsil etmesi için izin nesnesinin durum verilerini başlatmanız gerekir. Örneğin, bir <xref:System.Security.Permissions.FileIOPermission> nesne oluştururken, tüm dosyalara sınırsız erişimi veya dosyalara erişimi temsil etmesi için **DosyaIOPermission** nesnesini başlatmak için oluşturucuyu kullanabilirsiniz. Veya, nesnenin temsil etmesini istediğiniz erişim türünü (diğer bir şekilde okuma, ekleme veya yazma) ve nesnenin hangi dosyaları korumasını istediğinizi gösteren parametreleri geçirerek farklı bir **FileIOPermission** nesnesi kullanabilirsiniz.

Tek bir güvenlik nesnesini çağırmak için zorunlu güvenlik sözdizimini kullanmanın yanı sıra, izin kümesindeki bir izin grubunu başlatmak için kullanabilirsiniz. Örneğin, bu teknik, tek bir yöntemde birden çok izinde [ileri aramaları](using-the-assert-method.md) güvenilir bir şekilde gerçekleştirmenin tek yoludur. İzinler <xref:System.Security.PermissionSet> <xref:System.Security.NamedPermissionSet> grubu oluşturmak için ve sınıfları kullanın ve ardından istenen güvenlik çağrısını çağırmak için uygun yöntemi arayın.

Talepleri gerçekleştirmek ve geçersiz kılabilir, ancak istekleri geçersiz kılmak için zorunlu sözdizimini kullanabilirsiniz. İzin durumunu niçin başlatmanız gereken bilgiler yalnızca çalışma zamanında bilindiğinde bildirimsel sözdizimi yerine talepler ve geçersiz kılmalar için zorunlu sözdizimini kullanabilirsiniz. Örneğin, arayanların belirli bir dosyayı okuma iznine sahip olduğundan emin olmak istiyorsanız, ancak çalışma süresine kadar bu dosyanın adını bilmiyorsanız, zorunlu bir talep kullanın. Ayrıca, bir koşulun çalışma zamanında tutup tutmayacağını belirlemeniz ve test sonucuna bağlı olarak bir güvenlik talebi (veya değil) yapmanız gerektiğinde bildirimsel denetimler yerine zorunlu denetimler kullanmayı da seçebilirsiniz.

Aşağıdaki kod parçası, kodunuzun arayanların özel bir izninin bulunmasını `MyPermission`istemek için zorunlu sözdizimini gösterir. Bu izin varsayımsal bir özel izindir ve .NET Framework'de bulunmaz. Güvenlik çağrısı `MyPermission` ile yalnızca `MyMethod`bu yöntemi koruyarak, yeni bir örnek oluşturulur.

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

Çoğu uygulama ve bileşen (güvenli kitaplıklar hariç) doğrudan yönetilmeyen kodu çağırmamalıdır. Bunun çeşitli nedenleri vardır. Kod yönetilmeyen kodu doğrudan çağırırsa, kod yerel kodu çağırmak için yüksek düzeyde güven verilmesi gerektiğinden, birçok durumda çalışmasına izin verilmez. İlke, böyle bir uygulamanın çalışmasına izin verecek şekilde değiştirilirse, sistemin güvenliğini önemli ölçüde zayıflatabilir ve uygulamayı hemen hemen her işlemi gerçekleştirmek için ücretsiz bırakabilir.

Ayrıca, yönetilmeyen koda erişim izni olan kod, yönetilmeyen bir API'ye çağırarak büyük olasılıkla hemen hemen her işlemi gerçekleştirebilir. Örneğin, yönetilmeyen kodu arama izni olan kodun bir dosyaya erişmesi gerekmez; <xref:System.Security.Permissions.FileIOPermission> sadece doğrudan yönetilmeyen bir (Win32) dosya API arayabilirsiniz, **FileIOPermission**gerektiren yönetilen dosya API atlayarak. Yönetilen kod yönetilmeyen koda arama iznine sahipse ve doğrudan yönetilmeyen koda çağrı yapıyorsa, çalışma süresi yönetilmeyen kodüzerinde bu tür kısıtlamaları uygulayamayacağından, güvenlik sistemi güvenlik kısıtlamalarını güvenilir bir şekilde uygulayamaz.

Uygulamanızın yönetilmeyen koda erişmeyi gerektiren bir işlem gerçekleştirmesini istiyorsanız, bunu gerekli işlevselliği saran güvenilir yönetilen bir sınıf aracılığıyla yapmalıdır (böyle bir sınıf varsa). Güvenli bir sınıf kitaplığında zaten varsa, sarmalayıcı sınıflarını kendiniz oluşturmayın. Aramayı yönetilmeyen koda dönüştürmesine izin verebilmek için yüksek derecede güven verilmesi gereken sarıcı sınıfı, arayanların uygun izinlere sahip olmasını istemekten sorumludur. Sarmalayıcı sınıfını kullanıyorsanız, kodunuzu yalnızca paketleyici sınıfının istediği izinleri istemesi ve izinlerinin verilmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](using-the-assert-method.md)
- [Kod Erişimi Güvenliği](code-access-security.md)
- [Kod Erişim Güvenliği Temelleri](code-access-security-basics.md)
- [Öznitelikler](../../standard/attributes/index.md)
- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../standard/metadata-and-self-describing-components.md)
