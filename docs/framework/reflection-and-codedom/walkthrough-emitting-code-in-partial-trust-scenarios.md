---
title: 'İzlenecek yol: Kısmi Güven Senaryolarında Kod Yayma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection emit, anonymously hosted dynamic methods
- partial trust, reflection
- partial trust, emitting dynamic methods
- reflection emit, partial trust scenarios
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8461e0a074e7bdf9e1e2631c3f65e16de7256fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399762"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>İzlenecek yol: Kısmi Güven Senaryolarında Kod Yayma
Yansıma yayma aynı API tam veya kısmi güvende kümesini kullanır, ancak bazı özellikler kısmen güvenilen kod özel izinleri gerektirir. Ayrıca, yansıma yayma ile kısmi güven ve güvenlik saydam derlemeleri tarafından kullanılmak üzere tasarlanmış bir özelliği anonim barındırılan dinamik yöntemler vardır.  
  
> [!NOTE]
>  Önce [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], gerekli kod yayma <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrağı. Varsayılan olarak bu izni dahil `FullTrust` ve `Intranet` adlandırılmış izin ayarlar, ancak içinde değil `Internet` izin kümesi. Yalnızca sahipse, bu nedenle, bir kitaplık kısmi güven kullanılabilecek <xref:System.Security.SecurityCriticalAttribute> özniteliği ve ayrıca yürütülen bir <xref:System.Security.PermissionSet.Assert%2A> yöntemi <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Kodlama hataları güvenlik açıklarını neden olabilir çünkü böyle kitaplıklarının dikkatli güvenlik incelemesi gerektirir. [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Kısmi güven senaryolarında kod oluşturma için tüm güvenlik taleplerini veren kendiliğinden ayrıcalıklı bir işlem değil olmadan yayınlaması için kod sağlar. Diğer bir deyişle, oluşturulan kod bunu yayar derleme'den daha fazla hiçbir izni yoktur. Güvenliği saydam kod yayma ve assert ihtiyacını ortadan kaldırır kitaplıkları böylece <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, böylece güvenli bir kitaplık yazma gibi kapsamlı güvenlik incelemesi gerektirmez.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   [Kısmen sınama kodu güvenilir basit bir korumalı alan ayarı](#Setting_up).  
  
    > [!IMPORTANT]
    >  Bu, kısmi güven kodda denemeniz için basit bir yoludur. Gerçekte güvenilmeyen konumlardan gelen kodu çalıştırmak için bkz: [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
-   [Kısmen güvenilir uygulama etki alanlarında kod çalıştırmasını](#Running_code).  
  
-   [Kullanarak anonim barındırılan dinamik yöntemleri yayma ve kısmi güvende kod yürütmek için](#Using_methods).  
  
 Kısmi güven senaryolarında kod yayma hakkında daha fazla bilgi için bkz: [yansıma yayma güvenlik sorunları](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Bu yordamda gösterildiği kodu tam listesi için bkz: [örnek bölümüne](#Example) bu kılavuzun sonunda.  
  
<a name="Setting_up"></a>   
## <a name="setting-up-partially-trusted-locations"></a>Kısmen güvenilen konumları ayarlama  
 Aşağıdaki iki yordamdan kısmi güven koduyla test konumları ayarlama gösterilmektedir.  
  
-   İlk yordam bir korumalı uygulama etki alanı kodu Internet izinleri verilir oluşturulacağını gösterir.  
  
-   İkinci yordam nasıl ekleneceğini gösterir <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> eşit veya daha düşük güven derlemelerinin özel veri erişimi etkinleştirmek için bir kısmen güvenilir uygulama etki alanı için bayrak.  
  
### <a name="creating-sandboxed-application-domains"></a>Korumalı uygulama etki alanları oluşturma  
 Derlemeleriniz kısmi güven çalıştığı uygulama etki alanı oluşturmak için derlemeleri kullanılarak verilmesi için izinler kümesini belirtin <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> uygulama etki alanı oluşturmak için yöntemi aşırı yüklemesini. Verme kümesi belirtmek için kolay bir adlandırılmış izin Güvenlik İlkesi'nden kümesini almak için yoludur.  
  
 Aşağıdaki yordam, kısmi güven senaryoları verilmiş kod yalnızca Genel üyeler genel türleri erişebilmeniz için test etmek için kodunuzun çalıştığı bir korumalı uygulama etki alanı oluşturur. Bir sonraki yordamı nasıl ekleneceğini gösterir <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, hangi verilmiş kod erişebileceği ortak olmayan türleri ve üyeleri eşit veya daha düşük izinlerin verildiğini derlemelerde senaryolarını sınamak için.  
  
##### <a name="to-create-an-application-domain-with-partial-trust"></a>Kısmi güven uygulama etki alanı oluşturmak için  
  
1.  Bir izin korumalı uygulama etki alanı derlemelerde vermek kümesi oluşturun. Bu durumda, Internet bölgesi izin kümesi kullanılır.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2.  Oluşturma bir <xref:System.AppDomainSetup> nesne uygulama etki alanı ile bir uygulama yolu başlatılamadı.  
  
    > [!IMPORTANT]
    >  Kolaylık olması için bu kod örneği, geçerli klasörde kullanır. Gerçekte Internet'ten gelen kodu çalıştırmak için ayrı bir klasör güvenilmeyen kodunu açıklandığı gibi kullanmak [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3.  Uygulama etki alanı kurulum bilgileri ve uygulama etki alanında yürütme tüm derlemeler için ayarlanmış grant belirtme uygulama etki alanı oluşturun.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Son parametresi, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini verme kümesi uygulama etki alanının yerine tam güven verilecek olan derlemelerin kümesini belirtmenize olanak sağlar. Belirtmek zorunda değilsiniz [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] bu derlemeleri genel derleme önbelleğinde olduğundan, uygulamanızın, kullandığı derlemeler. Genel derleme önbelleğinde her zaman tam güvenilir. Genel derleme önbelleğinde olmayan tanımlayıcı adlı derlemeler belirtmek için bu parametreyi kullanın.  
  
### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Korumalı etki alanlarına RestrictedMemberAccess ekleme  
 Ana bilgisayar uygulamaları güven düzeyleri eşit veya bu kod yayar derleme güven düzeyini değerinden olan derlemeler özel verilere erişim sağlamak anonim barındırılan dinamik yöntemler izin verebilirsiniz. Tam zamanında (JIT) görünürlük denetimlerini kısıtlı özelliği etkinleştirmek için ana bilgisayar uygulaması ekler bir <xref:System.Security.Permissions.ReflectionPermission> nesnesi ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> verme kümesi (Madde iade) bayrak.  
  
 Örneğin, böylece Internet uygulamasını kendi derlemeler özel verilere eriştiğinde kod yayma bir konak Internet uygulamaları Internet izinleri artı Madde iade, izin verebilir. Erişim eşit veya daha düşük güven derlemeler için sınırlı olduğundan, Internet uygulamasını tam güvenilir derlemeler üyeleri gibi erişemiyor [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeler.  
  
> [!NOTE]
>  Anonim barındırılan dinamik yöntemler oluşturulan ayrıcalıkların önlemek için yığın bilgileri verme derleme için dahil edilir. Yöntem çağrıldığında, yığın bilgileri denetlenir. Bu nedenle, tam güvenilen koddan çağrılan bir anonim barındırılan dinamik verme derleme güven düzeyini hala sınırlı yöntemidir.  
  
##### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Kısmi güven artı Madde iade ile bir uygulama etki alanı oluşturmak için  
  
1.  Yeni bir <xref:System.Security.Permissions.ReflectionPermission> nesnesi ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (Madde iade) bayrak ve kullanmak <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> izin verme kümesine eklemek için yöntem.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     <xref:System.Security.PermissionSet.AddPermission%2A> Yöntemi zaten dahil edilmezse ayarlamak grant izni ekler. İzin verme kümesinde zaten varsa, belirtilen bayrakları varolan izni eklenir.  
  
    > [!NOTE]
    >  Madde iade anonim barındırılan dinamik yöntemler özelliğidir. Sıradan dinamik yöntemler JIT görünürlük denetimleri atlarsa verilmiş kodu tam güven gerektirir.  
  
2.  Uygulama etki alanı kurulum bilgileri ve grant belirtme uygulama etki alanı oluşturma ayarlayın.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## <a name="running-code-in-sandboxed-application-domains"></a>Korumalı uygulama etki alanlarında çalışan kod  
 Aşağıdaki yordam bir uygulama etki alanında yürütülebilecek yöntemleri kullanarak bir sınıf tanımlama, etki alanında sınıfının bir örneğini oluşturmak nasıl ve yöntemlerinden yürütmek nasıl açıklanmaktadır.  
  
#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Bir uygulama etki alanında bir yöntem yürütülmeye ve tanımlamak için  
  
1.  Türeyen bir sınıf tanımlama <xref:System.MarshalByRefObject>. Bu, diğer uygulama etki alanlarında sınıfının örneklerini oluşturmak ve uygulama etki alanı sınırlarında yöntemi çağrı yapmak için sağlar. Bu örnekte sınıfı adlı `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2.  Çalıştırmak istediğiniz kodu içeren bir ortak yöntemi tanımlayın. Bu örnekte, kod basit bir dinamik yöntem yayar, execute yöntemi için bir temsilci oluşturur ve temsilcisini çağırır.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3.  Ana programınız derlemenizi görünen adını alır. Örneklerini oluşturduğunuzda, bu ad kullanılır `Worker` korumalı uygulama etki alanında sınıfı.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4.  Bölümünde açıklandığı gibi bir korumalı uygulama etki alanı ana programınızı oluşturma [ilk yordam](#Setting_up) bu kılavuzda. Herhangi bir izin eklemek zorunda değilsiniz `Internet` izni ayarla, çünkü `SimpleEmitDemo` yöntemi yalnızca ortak yöntemlerini kullanır.  
  
5.  Ana programınız bir örneğini oluşturmak `Worker` korumalı uygulama etki alanında sınıfı.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Yöntemi hedef uygulama etki alanı nesnesi oluşturur ve özellikleri ve yöntemleri nesnenin çağırmak için kullanılan bir proxy döndürür.  
  
    > [!NOTE]
    >  Visual Studio'da bu kodu kullanırsanız, ad alanı içerecek şekilde sınıf adını değiştirmeniz gerekir. Varsayılan olarak, ad alanı, projeye adıdır. Örneğin, "PartialTrust" projesiyse sınıf adı "PartialTrust.Worker" olmalıdır.  
  
6.  Çağırmak için kodu ekleyin `SimpleEmitDemo` yöntemi. Uygulama etki alanı sınırından çağrı sıralanmış ve kod korumalı uygulama etki alanında yürütülür.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## <a name="using-anonymously-hosted-dynamic-methods"></a>Kullanarak anonim barındırılan dinamik yöntemler  
 Anonim barındırılan dinamik yöntemler sistem tarafından sağlanan saydam bir derleme ile ilişkilendirilmiş. Bu nedenle, içerdikleri kod saydamdır. Sıradan dinamik yöntemler, diğer yandan olmalıdır var olan bir modül ile ilişkili (doğrudan belirtilen veya ilişkili bir türünden olup olmadığını) ve güvenlik düzeylerini bu modülden gerçekleştirin.  
  
> [!NOTE]
>  Dinamik yöntemi anonim barındırma sağlar derleme ile ilişkilendirmek için tek yolu aşağıdaki yordamda açıklanan oluşturucular kullanmaktır. Bu gibi durumlarda, bir modül açıkça anonim barındırma derlemede belirtemezsiniz.  
  
 Sıradan dinamik yöntemleri ile ilişkili modülün iç üyelere veya ile ilişkili türün özel üyeleri erişebilir. Anonim barındırılan dinamik yöntemler diğer koddan yalıtılmış olduğundan, bunlar özel verilere erişimi. Ancak, özel verilere erişmek için JIT görünürlük denetimlerini atlamak için sınırlı bir özelliği vardır. Güven düzeyleri eşit veya bu kod yayar derleme güven düzeyini değerinden olan derlemeler bu yeteneği sınırlıdır.  
  
 Anonim barındırılan dinamik yöntemler oluşturulan ayrıcalıkların önlemek için yığın bilgileri verme derleme için dahil edilir. Yöntem çağrıldığında, yığın bilgileri denetlenir. Tam güvenilen koddan çağrılan anonim barındırılan dinamik bir yöntemi, gösterilen derleme güven düzeyini sınırlıdır.  
  
#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Anonim olarak kullanmak için barındırılan dinamik yöntemler  
  
-   Anonim barındırılan dinamik yöntemi bir ilişkilendirilmiş modülü ya da türü belirtmeyen bir Oluşturucu kullanarak oluşturun.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Anonim barındırılan dinamik yöntemi yalnızca genel türler ve yöntemler kullanıyorsa, kısıtlı üye erişimi gerektirmez ve JIT görünürlük denetimlerini gerekmez.  
  
     Özel izinler dinamik yöntemi yayma için gereklidir, ancak verilmiş kod türleri ve yöntemleri kullanır tarafından talep edilen izinler gerektirir. Örneğin, verilmiş kodu bir dosyaya eriştiğinde bir yöntemini çağırırsa, gerektirdiği <xref:System.Security.Permissions.FileIOPermission>. Güven düzeyi izni içermiyorsa verilmiş kod çalıştırıldığında bir güvenlik özel durum oluşur. Burada gösterilen kodu yalnızca kullanan dinamik bir yöntem yayar <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yöntemi. Bu nedenle, kodun, kısmen güvenilen konumlardan çalıştırılabilir.  
  
-   Alternatif olarak, JIT görünürlük denetimleri kullanarak atlamak için kısıtlı yeteneği olan bir anonim barındırılan dinamik yöntemi oluşturun <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> oluşturucusu ve belirterek `true` için `restrictedSkipVisibility` parametresi.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     Anonim barındırılan dinamik yöntemi yalnızca güven düzeyleri eşit veya verme derleme güven düzeyini değerinden sahip derlemelerde özel verilere erişebilmesini kısıtlamadır. Örneğin, dinamik yöntemi Internet güvenle yürütüyor, ayrıca Internet güvenle yürütülen diğer derlemelerden özel verilerine erişebilir, ancak özel verilerin erişemiyor [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeler. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeleri genel derleme önbelleğinde yüklenir ve her zaman tam güvenilir.  
  
     Anonim barındırılan dinamik yöntemler yalnızca ana bilgisayar uygulamasını verirse JIT görünürlük denetimlerini atlamak için kısıtlı özelliği kullanabilir <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı. Yöntem çağrıldığında bu izin için isteğe bağlı hale getirilir.  
  
    > [!NOTE]
    >  Dinamik yöntemi oluşturulduğunda çağrı yığını bilgileri verme derleme için dahil edilmiştir. Bu nedenle, talep verme derleme yöntemi çağırır derleme yerine izinleriyle karşı yapılır. Bu, verilmiş kodu yükseltilmiş izinlerle yürütülen önler.  
  
     [Tam kod örneği](#Example) bu kılavuzun sonunda kullanın ve kısıtlı üye erişimi sınırlamaları gösterir. Kendi `Worker` sınıfı anonim barındırılan dinamik yöntemler ile veya olmadan sınırlı görünürlük denetimlerini olanağı oluşturabilirsiniz bir yöntem içerir ve bu yöntem farklı uygulama etki alanında yürütmenin sonucu örnek gösterir güven düzeyleri.  
  
    > [!NOTE]
    >  Kısıtlı görünürlük denetimlerini olanağı anonim barındırılan dinamik yöntemler özelliğidir. Sıradan dinamik yöntemler JIT görünürlük denetimleri atlarsa tam güven verilmelidir.  
  
<a name="Example"></a>   
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneğinde kullanımını gösteren <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> anonim olarak izin vermek için bayrağı barındırılan ancak hedef üye kodu yayar derleme daha güven eşit veya daha düşük bir düzeyde olduğunda yalnızca JIT görünürlük denetimlerini atlamak için dinamik yöntemleri.  
  
 Örnek tanımlayan bir `Worker` uygulama etki alanı sınırlarında sıralanabilir sınıfı. Sınıfın iki sahip `AccessPrivateMethod` yayma ve dinamik bir yöntem yürütülemez yöntemi aşırı. İlk aşırı özel çağıran bir dinamik yöntemi yayar `PrivateMethod` yöntemi `Worker` sınıfı ve dinamik yöntemi ile veya olmadan JIT görünürlük denetimleri yayma. İkinci aşırı erişen dinamik bir yöntem yayar bir `internal` özelliği (`Friend` özelliğine Visual Basic'te), <xref:System.String> sınıfı.  
  
 Örnek, sınırlı ayarlamak grant oluşturmak için yardımcı bir yöntem kullanır. `Internet` izinleri ve bir uygulama etki alanı oluşturur kullanarak <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> etki alanında yürüten tüm kod bu verme kümesi kullandığını belirlemek için yöntemi aşırı yüklemesini. Örnek bir örneğini oluşturur `Worker` sınıfı uygulama etki alanında ve yürütür `AccessPrivateMethod` yöntemi iki kez.  
  
-   İlk kez `AccessPrivateMethod` yöntemi yürütüldüğünde, JIT görünürlük denetimleri zorlanmaz. Çağrıldığında, JIT görünürlük denetimleri özel yöntem erişimini engellemek için dinamik yöntemi başarısız olur.  
  
-   İkinci kez `AccessPrivateMethod` yöntemi yürütüldüğünde, JIT görünürlük denetimleri atlanır. Derlendiğinde, çünkü dinamik yöntem başarısız `Internet` kümesi görünürlük denetimlerini atlamak için yeterli izinleri vermez verin.  
  
 Örnek, <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> grant ayarlayın. Örnek sonra ikinci bir etki alanı oluşturur, tüm kodu, etki alanında yürütür belirterek yeni verme kümesi izinler verilir. Örnek bir örneğini oluşturur `Worker` sınıfının yeni bir uygulama etki alanında ve her iki aşırı yürütür `AccessPrivateMethod` yöntemi.  
  
-   İlk aşırı yüklemesini `AccessPrivateMethod` yöntemi yürütüldüğünde ve JIT görünürlük denetler atlanır. Dinamik yöntemi derler ve kod yayar derleme özel yöntem içeren derlemenin aynı olduğundan başarıyla yürütür. Bu nedenle, güven düzeyleri eşit. Uygulama, içeriyorsa `Worker` sınıfı birkaç derlemeleri açmış olduğunuz, bunların tümü aynı güven düzeyinde olacağından aynı işlemi bu derlemeler herhangi biri için başarılı.  
  
-   İkinci aşırı yüklemesini `AccessPrivateMethod` yöntemi yürütüldüğünde ve yeniden atlanır JIT görünürlük denetler. Bu süre dinamik yöntem, derlendiğinde, erişmeye çalıştığı için başarısız `internal` `FirstChar` özelliği <xref:System.String> sınıfı. İçeren derlemenin <xref:System.String> sınıftır tam güvenilir. Bu nedenle, daha yüksek bir güven düzeyi kodu yayar derleme daha altındadır.  
  
 Bu karşılaştırma gösterir nasıl <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> etkinleştirir kısmen güvenilen kod görünürlük atlamak için güvenilen kod güvenliği tehlikeye atmadan diğer kısmen güvenilen kod için denetler.  
  
### <a name="code"></a>Kod  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Visual Studio'da bu kod örneği oluşturmak için geçirdiğinizde ad alanı içerecek şekilde sınıfın adını değiştirmeniz gerekir <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> yöntemi. Varsayılan olarak, ad alanı, projeye adıdır. Örneğin, "PartialTrust" projesiyse sınıf adı "PartialTrust.Worker" olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yansıma Yaymadaki Güvenlik Sorunları](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [Nasıl yapılır: korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
