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
ms.openlocfilehash: bbf97b3bc72a12f8920e3a3cace3f7c31ed1e71a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910980"
---
# <a name="code-access-security-basics"></a>Kod Erişim Güvenliği Temelleri

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Ortak dil çalışma zamanını (yani, her yönetilen uygulama) hedefleyen her uygulama çalışma zamanının güvenlik sistemiyle etkileşmelidir. Yönetilen bir uygulama yüklendiğinde, ana bilgisayar otomatik olarak buna bir izin kümesi atar. Bu izinler konağın yerel güvenlik ayarlarına veya uygulamanın bulunduğu korumalı alana göre belirlenir. Bu izinlere bağlı olarak, uygulama düzgün şekilde çalışır veya bir güvenlik özel durumu oluşturur.

Masaüstü uygulamaları için varsayılan konak kodun tam güvende çalışmasına izin verir. Bu nedenle, uygulamanız masaüstünü hedefliyorsa, sınırsız bir izin kümesine sahiptir. Diğer konaklar veya korumalı uygulamalar için sınırlı bir izin kümesi sağlar. İzin kümesi konaktan konağa değiştirebildiğinden, uygulamanızı yalnızca hedef ana bilgisayarın izin verdiği izinleri kullanacak şekilde tasarlamanız gerekir.

Ortak dil çalışma zamanını hedefleyen etkili uygulamalar yazmak için aşağıdaki kod erişimi güvenlik kavramlarını bilmeniz gerekir:

- **Tür kullanımı uyumlu kod**: Tür kullanımı uyumlu kod yalnızca iyi tanımlanmış ve izin verilen yollarla türlere erişen koddur. Örneğin, geçerli bir nesne başvurusu verildiğinde, tür kullanımı uyumlu kod, gerçek alan üyelerine karşılık gelen sabit uzaklıklarda belleğe erişebilir. Kod, bu nesnenin genel kullanıma sunulan alanlarına ait bellek aralığının dışında rastgele uzaklıklarda belleğe erişirse, tür açısından güvenli değildir. Kod erişim güvenliği avantajlarından yararlanabilmek için kod sağlamak üzere, doğrulanabilir tür kullanımı uyumlu kod üreten bir derleyici kullanmanız gerekir. Daha fazla bilgi için bu konunun ilerleyen kısımlarında bulunan [Verifili tür kullanımı güvenli kod](#typesafe_code) bölümüne bakın.

- **Kesinlik ve bildirim temelli sözdizimi**: Ortak dil çalışma zamanını hedefleyen kod, izinleri isteyerek güvenlik sistemiyle etkileşime geçebilir, çağıranların izin verdiği ve belirli güvenlik ayarlarının geçersiz kılınması (yeterli ayrıcalık). .NET Framework güvenlik sistemi ile programlı olarak etkileşimde bulunmak için iki sözdizimi biçimi kullanırsınız: bildirime dayalı sözdizimi ve kesinlik temelli sözdizimi. Bildirim temelli çağrılar, öznitelikler kullanılarak gerçekleştirilir; zorunlu çağrılar, kodunuzun içindeki yeni sınıf örnekleri kullanılarak gerçekleştirilir. Bazı çağrılar yalnızca imperatively gerçekleştirilebilir, diğerleri yalnızca bildirimli olarak gerçekleştirilebilir ve bazı çağrılar her iki şekilde gerçekleştirilebilir.

- **Güvenli sınıf kitaplıkları**: Güvenli bir sınıf kitaplığı, kitaplığın arayanların, kitaplığın sunduğu kaynaklara erişim izni olduğundan emin olmak için güvenlik taleplerini kullanır. Örneğin, güvenli bir sınıf kitaplığı, arayanların dosya oluşturmak için izinlere sahip olduğunu talep eden dosyalar oluşturmak için bir yönteme sahip olabilir. .NET Framework, güvenli sınıf kitaplıklarından oluşur. Kodunuzun kullandığı herhangi bir kitaplığa erişmek için gereken izinlere dikkat etmeniz gerekir. Daha fazla bilgi için bu konunun ilerleyen kısımlarında [güvenli sınıf kitaplıklarını kullanma](#secure_library) bölümüne bakın.

- **Saydam kod**: .NET Framework 4 ' ten başlayarak, belirli izinleri tanımlamaya ek olarak kodunuzun güvenlik açısından saydam olarak çalıştırılıp çalıştırılmayacağını de belirlemelisiniz. Güvenliği saydam kod, güvenlik açısından kritik olarak tanımlanan türleri veya üyeleri çağıramaz. Bu kural, kısmen güvenilen uygulamaların yanı sıra tam güvenle uygulamalara da uygulanır. Daha fazla bilgi için bkz. [güvenlik-saydam kod](../../../docs/framework/misc/security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Verifi, türü güvenli kod yazma

Tam zamanında (JıT) derleme kodu inceleyen ve kodun tür açısından güvenli olup olmadığını belirlemeyi denediğinde doğrulama işlemini gerçekleştirir. Tür kullanımı için doğrulama sırasında kanıtlanmış koda, doğruıolarak *tür kullanımı güvenli kod*denir. Kod türü güvenli olabilir, ancak doğrulama işleminin veya derleyicinin sınırlamaları nedeniyle, tam olarak tür kullanımı güvenli olmayabilir. Dillerin hepsi tür açısından güvenli değildir ve Microsoft Visual C++gibi bazı dil derleyicileri tür kullanımı güvenli yönetilen kod üretemiyor. Kullandığınız dil derleyicisinin, doğruıya türü güvenli kod oluşturup oluşturmayacağını öğrenmek için derleyicinin belgelerine başvurun. Yalnızca belirli dil yapılarından kaçındığınızda, doğruıda tür açısından güvenli kod üreten bir dil derleyicisi kullanırsanız, kodunuzun doğruıya türü güvenli olup olmadığını anlamak için [PEVerify aracını](../../../docs/framework/tools/peverify-exe-peverify-tool.md) kullanmak isteyebilirsiniz.

Güvenlik ilkesi kodun doğrulamayı atlamasına izin veriyorsa, doğruısiz tür kullanımı güvenli olmayan kod yürütmeyi deneyebilir. Ancak, tür güvenliği çalışma zamanının derlemeleri yalıtma mekanizmasından önemli bir parçası olduğundan, kod güvenlik tür kurallarını ihlal ederse güvenlik güvenilir bir şekilde zorlanamaz. Varsayılan olarak, tür kullanımı güvenli olmayan kodun yalnızca yerel bilgisayardan geldiği durumlarda çalışmasına izin verilir. Bu nedenle, mobil kod tür kullanımı uyumlu olmalıdır.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Güvenli sınıf kitaplıklarını kullanma

Kodunuz isteklerinize ve sınıf kitaplığı için gereken izinlere izin verildiyse, bu, kitaplığa erişmesine izin verilir ve kitaplığın açığa çıkardığı kaynaklar yetkisiz erişimlerden korunacaktır. Kodunuzun uygun izinleri yoksa, sınıf kitaplığına erişimine izin verilmez ve kötü amaçlı kod, korumalı kaynaklara dolaylı olarak erişmek için kodunuzu kullanamaz. Kodunuzu çağıran diğer kodun de kitaplığa erişim izni olması gerekir. Aksi takdirde, kodunuzun çalışması da kısıtlanır.

Kod erişimi güvenliği, kod yazarken insan hatası olasılığını ortadan kaldırmaz. Ancak, uygulamanız korumalı kaynaklara erişmek için güvenli sınıf kitaplıkları kullanıyorsa, uygulama kodu için güvenlik riski azalır, çünkü sınıf kitaplıkları olası güvenlik sorunları için yakından scrutinized.

## <a name="declarative-security"></a>Bildirim Temelli Güvenlik

Bildirime dayalı güvenlik sözdizimi, güvenlik bilgilerini kodunuzun [meta verilerine](../../standard/metadata-and-self-describing-components.md) yerleştirmek için [özniteliklerini](../../standard/attributes/index.md) kullanır. Öznitelikleri, kullanmak istediğiniz istek, talep veya geçersiz kılma türünü belirtmek için derleme, sınıf veya üye düzeyinde yerleştirilebilir. İstekler, çalışma zamanı güvenlik sistemini, uygulamanızın ihtiyacı olan veya istemediğiniz izinlerle ilgili bilgilendirmek için ortak dil çalışma zamanını hedefleyen uygulamalarda kullanılır. Talepler ve geçersiz kılmalar, kaynakların çağıranlara karşı korunmasına yardımcı olmak veya varsayılan güvenlik davranışını geçersiz kılmak için kitaplıklarda kullanılır.

> [!NOTE]
> .NET Framework 4 ' te, .NET Framework güvenlik modelinde ve terminolojisinde önemli değişiklikler yapıldı. Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).

Bildirim temelli güvenlik çağrıları kullanmak için, izin nesnesinin durum verilerini, ihtiyacınız olan belirli bir izin biçimini temsil etmek üzere başlatmalısınız. Her yerleşik izin, gerçekleştirmek istediğiniz güvenlik işleminin türünü tanımlayan bir <xref:System.Security.Permissions.SecurityAction> sabit listesi geçen bir özniteliğe sahiptir. Ancak izinler, kendilerine özel olan kendi parametrelerini de kabul eder.

Aşağıdaki kod parçası, kodunuzun çağıranlarının adlı `MyPermission`özel bir izni olmasını istemek için bildirime dayalı sözdizimi gösterir. Bu izin kuramsal bir özel izindir ve .NET Framework yok. Bu örnekte, bildirim temelli çağrı doğrudan sınıf tanımından yerleştirilir ve bu iznin sınıf düzeyine uygulanacağını belirtin. Bu özniteliğe, çağıranların çalıştırılabilmesi için bu izne sahip olması gerektiğini belirtmek üzere bir **SecurityAction. Demand** yapısı geçirilir.

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

Kesinlik temelli güvenlik sözdizimi, çağırmak istediğiniz izin nesnesinin yeni bir örneğini oluşturarak bir güvenlik çağrısı yayınlar. Talepler ve geçersiz kılmalar gerçekleştirmek için zorunlu sözdizimi kullanabilirsiniz ancak istekler için izin vermez.

Güvenlik çağrısını yapmadan önce, izin nesnesinin durum verilerini, ihtiyacınız olan iznin belirli bir biçimini temsil etmek üzere başlatmalısınız. Örneğin, bir <xref:System.Security.Permissions.FileIOPermission> nesne oluştururken, tüm dosyalara Kısıtlanmamış erişimi veya dosyalara erişimi temsil edebilmesi için, **filei, görev** nesnesini başlatmak üzere oluşturucuyu kullanabilirsiniz. Ya da, nesnenin temsil etmesini istediğiniz erişim türünü (yani oku, Ekle veya yaz) ve nesnenin hangi dosyaları koruyacağınızı belirten parametreleri geçirerek farklı bir **dosya adlı görev** nesnesi kullanabilirsiniz.

Tek bir güvenlik nesnesini çağırmak için zorunlu güvenlik sözdizimi kullanmanın yanı sıra, bir izin kümesindeki bir grup izinleri başlatmak için kullanabilirsiniz. Örneğin, bu teknik, tek bir yöntemde birden çok izne yapılan [](../../../docs/framework/misc/using-the-assert-method.md) onay çağrılarını güvenilir bir şekilde gerçekleştirmenin tek yoludur. <xref:System.Security.PermissionSet> Ve<xref:System.Security.NamedPermissionSet> sınıflarını kullanarak bir grup izin oluşturun ve ardından istenen güvenlik çağrısını çağırmak için uygun yöntemi çağırın.

Talepler ve geçersiz kılmalar gerçekleştirmek için zorunlu sözdizimi kullanabilirsiniz ancak istekler için izin vermez. İzin durumunu başlatmak için ihtiyaç duyduğunuz bilgiler yalnızca çalışma zamanında bilindiğinde bildirime dayalı sözdizimi yerine talepler ve geçersiz kılmalar için tanımlayıcı sözdizimini kullanabilirsiniz. Örneğin, çağıranların belirli bir dosyayı okuma izni olduğundan emin olmak istiyorsanız, ancak çalışma zamanına kadar bu dosyanın adını bilemezsiniz, bir zorunlu talep kullanın. Ayrıca, bir koşulun sahip olup olmadığını ve testin sonucuna bağlı olarak, bir güvenlik talebi (veya değil), çalışma zamanında belirlemeniz gerektiğinde, bildirim temelli denetimler yerine zorunlu denetimleri kullanmayı seçebilirsiniz.

Aşağıdaki kod parçası, kodunuzun çağıranlarının adlı `MyPermission`özel bir izni olmasını istemek için zorunlu sözdizimi gösterir. Bu izin kuramsal bir özel izindir ve .NET Framework yok. Yalnızca güvenlik çağrısıyla birlikte `MyPermission` bu yöntemin korunması `MyMethod`içinde yeni bir örneği oluşturulur.

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

Çoğu uygulama ve bileşen (Güvenli Kitaplıklar hariç), yönetilmeyen kodu doğrudan çağırmamalıdır. Bunun birçok nedeni vardır. Kod doğrudan yönetilmeyen kodu çağırırsa, koda yerel kod çağırmak için yüksek düzeyde güven verilmesi gerektiğinden birçok durumda çalışmasına izin verilmez. İlke böyle bir uygulamanın çalışmasına izin verecek şekilde değiştirilirse, neredeyse tüm işlemleri gerçekleştirmek için uygulamayı ücretsiz bırakarak sistemin güvenliğini önemli ölçüde yumuşalabilir.

Ayrıca, yönetilmeyen koda erişim izni olan kod muhtemelen yönetilmeyen bir API 'ye çağırarak neredeyse tüm işlemleri gerçekleştirebilir. Örneğin, yönetilmeyen kodu çağırma iznine sahip olan kodun bir dosyaya erişmesi gerekmez <xref:System.Security.Permissions.FileIOPermission> ; dosya API 'sini atlayarak yalnızca yönetilmeyen (Win32) dosya API 'sini doğrudan çağırabilir. Yönetilen kodun yönetilmeyen koda çağrı yapmak ve doğrudan yönetilmeyen koda çağrı yapmak için izni varsa, güvenlik sistemi güvenlik kısıtlamalarını güvenilir bir şekilde zorlayamayacak ve bu nedenle çalışma zamanı, yönetilmeyen koddaki kısıtlamaları zorlayamıyor.

Uygulamanızın yönetilmeyen koda erişmesi gereken bir işlem gerçekleştirmesini istiyorsanız, bu işlemi gerekli işlevleri sarmalayan güvenilir bir yönetilen sınıf (böyle bir sınıf varsa) ile gerçekleştirir. Güvenli bir sınıf kitaplığında zaten varsa sarmalayıcı sınıf oluşturmayın. Yönetilmeyen koda çağrı yapmasına izin verilmesi gereken yüksek ölçüde güven gerektiren sarmalayıcı sınıfına, arayanların uygun izinlere sahip olduğundan emin olmanız gerekir. Sarmalayıcı sınıfını kullanırsanız, kodunuzun yalnızca istemesi gerekir ve sarmalayıcı sınıfının talep verdiği izinler verilmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Vermediğini](../../../docs/framework/misc/using-the-assert-method.md)
- [Kod erişim güvenliği](../../../docs/framework/misc/code-access-security.md)
- [Kod erişim güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)
- [Öznitelikler](../../standard/attributes/index.md)
- [Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../standard/metadata-and-self-describing-components.md)
