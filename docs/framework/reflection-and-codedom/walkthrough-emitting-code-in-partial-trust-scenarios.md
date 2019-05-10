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
ms.openlocfilehash: 54a6a1cda604cb9cdeecd9587af81dbdb810965c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592448"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>İzlenecek yol: Kısmi Güven Senaryolarında Kod Yayma
Yansıma yayma aynı API kümesini tam veya kısmi güvende kullanır, ancak bazı özellikler kısmen güvenilen kodda özel izinler gerektirir. Ayrıca, yansıma yayılımı, güvenlikli saydam derlemeler tarafından kısmi güven ile kullanılmak üzere tasarlanmış bir özelliği, anonim olarak barındırılan dinamik yöntemler vardır.  
  
> [!NOTE]
>  Önce [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], kod yaymak <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrağı. Bu izin varsayılan olarak dahil edilen `FullTrust` ve `Intranet` adlandırılmış izin kümelerine, ancak içinde olmayan `Internet` izin kümesi. Yalnızca sahipse, bu nedenle, bir kitaplık kısmi güvenden kullanılabilir <xref:System.Security.SecurityCriticalAttribute> özniteliği ve ayrıca bir <xref:System.Security.PermissionSet.Assert%2A> yöntemi <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Kodlama hataları güvenlik açıklarına neden olabileceğinden tür kitaplıkların dikkatli bir güvenlik incelemesinden geçmesi gerekir. [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Çünkü kod oluşturma herhangi bir güvenlik talebi verme doğası gereği ayrıcalıklı bir işlem değil olmadan kısmi güvenlik senaryolarına yayılmasını sağlar. Diğer bir deyişle, oluşturulan kod, yayan derlemenin daha fazla izne sahiptir. Güvenliği saydam kod yayan ve ihtiyacını kaldırır kitaplıkları böylece <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, böylece güvenli bir kitaplık yazmak gibi kapsamlı bir güvenlik incelemesi gerektirmez.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- [Testi kısmen güvenilen kod basit bir korumalı alan ayarı](#Setting_up).  
  
    > [!IMPORTANT]
    >  Bu, kısmi güvenli kodla denemek için basit bir yoludur. Aslında güvenilmeyen konumlardan gelen kodu çalıştırmak için bkz: [nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
- [Kısmen güvenilir uygulama etki alanlarında kod çalıştırma](#Running_code).  
  
- [Anonim olarak barındırılan dinamik yöntemleri yayma ve kısmi güvende kod yürütmek için](#Using_methods).  
  
 Kısmi güven senaryolarında kod yayma hakkında daha fazla bilgi için bkz. [yansıma yayma güvenlik sorunları](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Bu yordamlarda gösterilen kod tam listesi için bkz. [örnek bölümünde](#Example) bu kılavuzun sonunda.  
  
<a name="Setting_up"></a>   
## <a name="setting-up-partially-trusted-locations"></a>Kısmen güvenilen konumları hazırlama  
 Aşağıdaki iki yordam, kısmi güven ile kodu test edebileceğiniz konumları ayarlama işlemini göstermektedir.  
  
- İlk yordam, kod Internet izinlerine sahip koruma alanlı uygulama etki alanı oluşturma gösterilmektedir.  
  
- İkinci yordam, ekleme işlemi açıklanır <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> eşit veya daha az Güve derlemeler içerisindeki özel verilere erişmesini etkinleştirmek için bir kısmen güvenilir uygulama etki alanı için bayrak.  
  
### <a name="creating-sandboxed-application-domains"></a>Koruma alanlı uygulama etki alanları oluşturma  
 Derlemelerinizin kısmi güvenle çalışacağı bir uygulama etki alanı oluşturmak için kullanarak derlemelere verilecek izin kümesi belirtmelisiniz <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesi, uygulama etki alanı oluşturmak için. İzin kümesini belirtmenin en kolay yolu, adlandırılmış bir izin kümesi Güvenlik İlkesi'nden almak sağlamaktır.  
  
 Aşağıdaki yordam yayılan kodun sadece genel türlerin ortak üyeler erişebildiği test senaryolarında için kısmi güven ile kodunuzu çalıştıran bir koruma alanlı uygulama etki alanı oluşturur. Sonraki yordam, ekleme işlemi açıklanır <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, hangi kodun erişebilir ortakdeğil türlere ve eşit veya daha az izin verilen derlemelerdeki üyeleri senaryolarını test etmek için.  
  
##### <a name="to-create-an-application-domain-with-partial-trust"></a>Kısmi güven ile bir uygulama etki alanı oluşturmak için  
  
1. Korumalı uygulama etki alanındaki derlemelere vermek amacıyla bir izin kümesi oluşturun. Bu durumda, Internet bölgesi izinleri kümesi kullanılır.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2. Oluşturma bir <xref:System.AppDomainSetup> uygulama etki alanını bir uygulama yoluyla başlatmak için nesne.  
  
    > [!IMPORTANT]
    >  Kolaylık olması için bu kod örneği geçerli klasörü kullanır. Aslında Internet'ten gelen kodu çalıştırmak için ayrı bir klasör güvenilmeyen kod için açıklandığı kullanın [nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3. Uygulama etki alanı kurulum bilgilerini ve uygulama etki alanında yürütülen tüm derlemeler için ayarlanmış vermeler belirleyen uygulama etki alanını oluşturun.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Son parametresi <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> yöntemi aşırı yükleme uygulama etki alanının izin kümeleri yerine tam güven verilmesi için bir derleme kümesi belirtmenize imkan tanır. Belirtmek zorunda değilsiniz [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] bu derlemeler genel derleme önbelleğinde olduğundan, uygulamanızın kullandığı derlemeler. Genel derleme önbelleğindeki derlemelere her zaman tamamen güvenilirdir. Bu parametre, genel derleme önbelleğinde olmayan tanımlayıcı adlı derlemeleri belirtmek için kullanabilirsiniz.  
  
### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Etki alanlarına RestrictedMemberAccess ekleme  
 Ana bilgisayar uygulamalarını güven düzeyleri eşittir veya daha az kodu yayan derlemenin güven düzeyine sahip derlemelerdeki özel verilere erişmesini sağlamak anonim olarak barındırılan dinamik yöntemler izin verebilirsiniz. Just-ın-time (JIT) görünürlük denetimlerini atlamak bu kısıtlı özelliği etkinleştirmek için ana bilgisayar uygulaması ekler. bir <xref:System.Security.Permissions.ReflectionPermission> nesnesi ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> izin kümesi (RMA) bayrak.  
  
 Örneğin, böylece bir Internet uygulaması kendi derlemelerindeki özel verilere erişen kodu yayar bir konak Internet uygulamaları Internet izinlerinin yanı sıra RMA, verebilir. Erişim eşit veya daha düşük güven derlemeleri için sınırlı olduğundan, bir Internet uygulaması tamamen güvenilir derlemelerinin üyelerine gibi erişemiyor [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeler.  
  
> [!NOTE]
>  Anonim olarak barındırılan dinamik yöntemler oluşturulduğunda ayrıcalık yükselmesini engellemek için yayan derleme için yığın bilgileri dahil edilir. Yöntem çağrıldığında, yığın bilgisi denetlenir. Bu nedenle, tam olarak güvenilen koddan çağrılan anonim olarak barındırılan dinamik bir yöntem yayan derlemenin güven düzeyine hala sınırlıdır.  
  
##### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Kısmi güvenli artı RMA'lı bir uygulama etki alanı oluşturmak için  
  
1. Yeni bir <xref:System.Security.Permissions.ReflectionPermission> nesnesi ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (RMA) kullanın <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> izin verme kümesine izin eklemek için yöntemi.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     <xref:System.Security.PermissionSet.AddPermission%2A> Yöntemi izin zaten dahil edilmezse kümelerine izin ekler. İzin izin verme kümesine zaten eklenmişse belirtilen bayraklar varolan izne eklenir.  
  
    > [!NOTE]
    >  RMA anonim olarak barındırılan dinamik yöntemlerin bir özelliğidir. Sıradan dinamik yöntemler, JIT görünürlük kontrollerini atladığında, verilmiş kod tam güven gerektirir.  
  
2. Uygulama etki alanı kurulum bilgilerini ve izin verme belirleyen uygulama etki alanını oluşturma ayarlayın.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## <a name="running-code-in-sandboxed-application-domains"></a>Koruma alanlı uygulama etki alanlarında kod çalıştırma  
 Aşağıdaki yordam nasıl bir uygulama etki alanında yürütülebilecek yöntemleri kullanarak bir sınıf tanımlamak, etki alanında sınıfının bir örneğini oluşturma ve yöntemlerini yürütmek nasıl açıklamaktadır.  
  
#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Tanımlama ve bir uygulama etki alanında bir yöntem yürütülmeye  
  
1. Türetilen bir sınıf tanımlama <xref:System.MarshalByRefObject>. Bu, diğer uygulama etki alanlarında sınıfın örneklerini oluşturmak ve uygulama etki alanı sınırları içerisinde yöntem çağrıları yapmak için sağlar. Bu örnekte sınıf adlı `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2. Yürütmek istediğiniz kodu içeren genel bir yöntemi tanımlayın. Bu örnekte, kod basit bir dinamik yöntem yayar, yöntemi yürütmek için bir temsilci oluşturur ve temsilci çağırır.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3. Ana programınızda, derlemenizin görünen adını alın. Bu ad örneklerini oluşturduğunuzda kullanılır `Worker` koruma alanlı uygulama etki alanındaki sınıfı.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4. Ana programınızda, korumalı uygulama etki alanı açıklandığı oluşturma [ilk yordam](#Setting_up) Bu izlenecek yolda. Herhangi bir izin eklemeniz gerekmez `Internet` izin kümesinin, çünkü `SimpleEmitDemo` yöntemi yalnızca genel yöntemler kullanır.  
  
5. Ana programınızda bir örneğini oluşturmak `Worker` koruma alanlı uygulama etki alanındaki sınıfı.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Yöntemi hedef uygulama alanı içerisindeki nesneyi oluşturur ve özellikleri ve nesnenin yöntemleri çağırmak için kullanılabilecek bir proxy döndürür.  
  
    > [!NOTE]
    >  Visual Studio'da bu kodu kullanırsanız, ad alanını katmak için sınıf adını değiştirmeniz gerekir. Varsayılan olarak, ad alanı projenin adıdır. Örneğin, proje "PartialTrust" ise, sınıf adı "PartialTrust.Worker" olmalıdır.  
  
6. Çağırmak için kod ekleyin `SimpleEmitDemo` yöntemi. Çağrı uygulama etki alanı sınırı ötesinde sıralanır ve kod korumalı uygulama etki alanında yürütülür.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## <a name="using-anonymously-hosted-dynamic-methods"></a>Kullanarak anonim olarak barındırılan dinamik metotlar  
 Anonim olarak barındırılan dinamik yöntemler, sistem tarafından sağlanan saydam bir derleme ile ilişkilendirilir. Bu nedenle, içerdikleri kod saydamdır. Sıradan dinamik yöntemler, diğer taraftan, olmalıdır varolan bir modülle (doğrudan belirtilen veya ilişkilendirilmiş bir türden çıkarılan olup olmadığını) ve güvenlik düzeylerini o modülden gerçekleştirin.  
  
> [!NOTE]
>  Dinamik bir yöntem anonim barındırma sağlayan derlemenin ilişkilendirilmesinin tek yolu Aşağıdaki prosedür içerisinde tanımlanan oluşturucuların kullanmaktır. Anonim barındırma derlemesinde açıkça bir modül belirtemezsiniz.  
  
 Sıradan dinamik yöntemler ilişkilendirildikleri modülün iç üyelerine veya ilişkilendirildikleri türün özel üyelerine erişebilir. Anonim olarak barındırılan dinamik yöntemler başka bir koddan ayrılmış olduğu için bunlar özel verilere erişiminiz yok. Ancak, bunlar özel verilere erişebilmek için JIT görünürlük denetimlerini atlamak için kısıtlı bir yeteneği vardır. Bu yetenek, eşit veya daha az kodu yayan derlemenin güven düzeyine güven düzeylerine sahip Derlemelerle sınırlıdır.  
  
 Anonim olarak barındırılan dinamik yöntemler oluşturulduğunda ayrıcalık yükselmesini engellemek için yayan derleme için yığın bilgileri dahil edilir. Yöntem çağrıldığında, yığın bilgisi denetlenir. Tamamen güvenilen koddan çağrılan anonim olarak barındırılan dinamik bir yöntem onu gösteren derlemenin güven düzeyine hala sınırlıdır.  
  
#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Kullanılacak anonim olarak barındırılan dinamik metotlar  
  
- Bir ilişkilendirilmiş modülü veya türü belirtmeyen bir kurucu kullanarak anonim olarak barındırılan bir dinamik yöntem oluşturun.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Anonim olarak barındırılan dinamik bir yöntem yalnızca genel türleri ve yöntemleri kullanıyorsa, sınırlandırılmış üye erişimini gerektirmez ve JIT görünürlük denetimlerini atlamak zorunda değildir.  
  
     Dinamik bir yöntem yaymak için özel izin gerekir ancak kullandığı kod türlerinin ve yöntemlerin tarafından talep izinleri gerektirir. Örneğin, yayılan kod dosyaya erişen bir yöntemini çağırırsa, gerektiriyorsa <xref:System.Security.Permissions.FileIOPermission>. Güven düzeyi izni yoksa, gösterilen kod çalıştırıldığında bir güvenlik özel durum oluşturulur. Burada gösterilen kod yalnızca kullanan bir dinamik yöntem yayar <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yöntemi. Bu nedenle, kod kısmen güvenilen konumlardan yürütülebilir.  
  
- Alternatif olarak, kullanarak JIT görünürlük denetimlerini atlamak için sınırlanmasıyla anonim olarak barındırılan dinamik bir yöntem oluşturmak <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> oluşturucusu ve belirterek `true` için `restrictedSkipVisibility` parametresi.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     Anonim olarak barındırılan dinamik yöntemin sadece güven düzeyine eşit veya daha az yayan derlemenin güven düzeyine sahip derlemeler içerisindeki özel verilere erişebilirsiniz kısıtlaması yoktur. Örneğin, dinamik yöntem Internet güveni ile yürütülüyorsa, aynı zamanda Internet güveni ile yürütülen diğer derlemelerdeki özel verilere erişebilirsiniz, ancak özel verilerine erişemez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeler. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeleri genel derleme önbelleğinde yüklü ve her zaman tamamen güvenilirdir.  
  
     Anonim olarak barındırılan dinamik yöntemler bu kısıtlı özelliği yalnızca ana uygulama verirse, JIT görünürlük denetimlerini atlamak için kullanabileceğiniz <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı. Yöntem çağrıldığında bu izin için talep yapılır.  
  
    > [!NOTE]
    >  Yayan derleme için çağrı yığını bilgisi dinamik yöntem oluşturulduğunda dahildir. Bu nedenle, talep, yöntemi çağıran derleme yerine yayan derlemenin izinlerine karşı yapılır. Bu, verilmiş kodun yükseltilmiş izinlerle yürütülmesini engeller.  
  
     [Tam kod örneği](#Example) bu kılavuzun sonunda ve kısıtlamalarını sınırlı üye erişiminin kullanımını gösterir. Kendi `Worker` sınıfı ile veya olmadan görünürlük denetimlerini atlamasını sınırlanmasıyla anonim olarak barındırılan dinamik yöntemler oluşturabileceğiniz bir yöntem içerir ve örnek farklı uygulama etki alanlarındaki bu yöntemi yürütme sonucunu göstermektedir. güven düzeyleri.  
  
    > [!NOTE]
    >  Görünürlük denetimlerini atlamasını sınırlanmasıyla anonim olarak barındırılan dinamik yöntemlerin bir özelliğidir. Sıradan dinamik yöntemler, JIT görünürlük kontrollerini atladığında, bunlar tam güven verilmesi gerekir.  
  
<a name="Example"></a>   
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> anonim olarak izin vermek için bayrağı barındırılan dinamik yöntemler, ancak hedef üye kodu yayan derlemenin güven eşit veya daha düşük bir düzeyde olduğunda yalnızca JIT görünürlük denetimlerini atlamak için.  
  
 Örnek tanımlayan bir `Worker` uygulama etki alanı sınırları ötesinde sıralanabilecek sınıfı. Sınıfı iki içeren `AccessPrivateMethod` yöntemi aşırı yüklemeleri yayan ve dinamik bir yöntem yürütülemez. İlk aşırı yükleme özel çağıran dinamik bir yöntem yayar `PrivateMethod` yöntemi `Worker` sınıfı ve ile veya JIT görünürlük denetimleri olmadan dinamik yöntemi yayabilir. İkinci aşırı yükleme erişen dinamik bir yöntem yayar bir `internal` özelliği (`Friend` özellik Visual Basic'te), <xref:System.String> sınıfı.  
  
 Örnek bir yardımcı yöntem için sınırlı bir izin kümesi oluşturmak için kullanır. `Internet` izinleri ve ardından bir uygulama etki alanı oluşturur kullanarak <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> yöntemi aşırı yüklemesi, etki alanında çalışan tüm kodun bu izin kümesini kullandığını belirtmek için. Örnek örneği oluşturur `Worker` sınıf uygulama etki alanında ve yürüten `AccessPrivateMethod` iki kez yöntemi.  
  
- İlk kez `AccessPrivateMethod` yöntemi yürütüldüğünde, JIT görünürlük denetimleri zorlanır. Çağrıldığında, JIT görünürlük denetimlerini, özel yönteme erişmesini engellediğinden dinamik yöntem başarısız olur.  
  
- İkinci kez `AccessPrivateMethod` yöntemi yürütüldüğünde, JIT görünürlük denetimleri atlanır. Dinamik yöntem derlendiğinde, çünkü başarısız `Internet` verme kümesi görünürlük denetimlerini atlamak için yeterli izin vermez.  
  
 Örnek ekler <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> izin kümesine. Bu örnek, ardından ikinci bir etki alanı oluşturur, tüm kod, etki alanında çalışan belirtme yeni izin kümesi izinler verilir. Örnek örneği oluşturur `Worker` sınıfının yeni bir uygulama etki alanında ve her iki yeniden yüklemesini yürütmektedir `AccessPrivateMethod` yöntemi.  
  
- İlk aşırı yüklemesini `AccessPrivateMethod` yöntemi yürütülür ve JIT görünürlük denetimleri atlanır. Dinamik yöntem derler ve kod yayan derlemenin özel yöntemi içeren derleme ile aynı olduğu için başarıyla yürütür. Bu nedenle, güven düzeyleri eşittir. Uygulama, içerip içermediğini `Worker` sınıfının yer aldığı çeşitli derlemeler, bunların tümü aynı güven düzeyinde olacağından bu derlemelerden herhangi biri için aynı işlem başarılı olabilir.  
  
- İkinci aşırı yüklemesi `AccessPrivateMethod` yöntemi yürütüldüğünde ve yeniden JIT görünürlük denetimleri atlanır. Bu süre dinamik yöntem, derlendiğinde, erişmeye çalıştığı için başarısız `internal` `FirstChar` özelliği <xref:System.String> sınıfı. İçeren derleme <xref:System.String> sınıfı, tam olarak güvenilir. Bu nedenle daha yüksek düzeyde güven kodu yayan derlemeden gereklidir.  
  
 Bu karşılaştırmayı gösteren nasıl <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> kısmen güvenilen görünürlük kontrollerini atlamasını diğer kısmen güvenilen kod için güvenli kodun güvenliğini tehlikeye atmadan etkinleştirir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu kod örneği Visual Studio'da derleme yaparsanız, kendisine geçirdiğiniz ad alanını katmak için sınıf adını değiştirmeniz gerekir <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> yöntemi. Varsayılan olarak, ad alanı projenin adıdır. Örneğin, proje "PartialTrust" ise, sınıf adı "PartialTrust.Worker" olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Yaymadaki Güvenlik Sorunları](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
