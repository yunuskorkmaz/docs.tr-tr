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
ms.openlocfilehash: 002434cf51b221a456c8752b5b1388912f875a28
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045749"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>İzlenecek yol: Kısmi Güven Senaryolarında Kod Yayma

Yansıma yayma, tam veya kısmi güvende aynı API kümesini kullanır, ancak bazı özellikler kısmen güvenilen kodda özel izinler gerektirir. Ayrıca, yansıma yayma özelliği, kısmi güvenle ve güvenlik açısından saydam derlemelerde kullanılmak üzere tasarlanan, anonim olarak barındırılan bir dinamik yöntem özelliğine sahiptir.

> [!NOTE]
> 3,5 .NET Framework önce, <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrak ile gerekli kodu yayma. Bu izin, `FullTrust` ve `Intranet` adlandırılmış izin kümelerinde varsayılan olarak dahil edilir `Internet` , ancak izin kümesinde yoktur. Bu nedenle, bir kitaplık yalnızca <xref:System.Security.SecurityCriticalAttribute> özniteliği varsa ve için <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>bir <xref:System.Security.PermissionSet.Assert%2A> Yöntem yürütülürse kısmi güvenle kullanılabilir. Bu tür Kitaplıklar, kodlama hataları güvenlik delikleri ile sonuçlanabileceğinden dikkatli bir güvenlik incelemesi gerektirir. .NET Framework 3,5, kod oluşturma doğal olarak ayrıcalıklı bir işlem olmadığından kodun herhangi bir güvenlik talebi vermeden kısmi güven senaryolarında oluşturulmasına olanak sağlar. Diğer bir deyişle, oluşturulan kodun onu yayan derlemeden daha fazla izni yoktur. Bu, kodu oluşturan kitaplıkların güvenlik açısından saydam olmasını sağlar ve güvenli bir kitaplık yazmak bu tür <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>kapsamlı bir güvenlik incelemesi gerektirmemesi için onay gereksinimini ortadan kaldırır.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Kısmen güvenilen kodu test etmek için basit bir korumalı alan ayarlama](#Setting_up).

  > [!IMPORTANT]
  > Bu, kısmi güvende kodla denemeler yapmanın basit bir yoludur. Gerçekten güvenilmeyen konumlardan gelen kodu çalıştırmak için bkz [. nasıl yapılır: Bir korumalı alanda](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)kısmen güvenilen kodu çalıştırın.

- [Kısmen güvenilen uygulama etki alanlarında kod çalıştırma](#Running_code).

- [Kısmi güvende kodu yaymak ve yürütmek için anonim olarak barındırılan dinamik yöntemler kullanma](#Using_methods).

Kısmi güven senaryolarında kod yayma hakkında daha fazla bilgi için, bkz. [yansıma yayma Içindeki güvenlik sorunları](security-issues-in-reflection-emit.md).

Bu yordamlarda gösterilen kodun tüm listesi için bu izlenecek yolun sonundaki [örnek bölümüne](#Example) bakın.

<a name="Setting_up"></a>

## <a name="setting-up-partially-trusted-locations"></a>Kısmen güvenilen konumlar ayarlama

Aşağıdaki iki yordamda, kodu kısmi güvenle test etmek için kullanabileceğiniz konumların nasıl ayarlanacağı gösterilmektedir.

- İlk yordam, koda Internet izinleri verilen bir korumalı uygulama etki alanı oluşturmayı gösterir.

- İkinci yordam, eşit veya daha az <xref:System.Security.Permissions.ReflectionPermission> güvenin derlemelerindeki özel verilere erişimi etkinleştirmek için kısmen güvenilen bir uygulama etki alanına <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> işaret ile nasıl ekleneceğini gösterir.

### <a name="creating-sandboxed-application-domains"></a>Korumalı uygulama etki alanları oluşturma

Derlemelerinizin kısmi güvenle çalıştırıldığı bir uygulama etki alanı oluşturmak için, uygulama etki alanını oluşturmak üzere <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> yöntem aşırı yüklemesini kullanarak derlemelere verilecek izin kümesini belirtmeniz gerekir. İzin kümesini belirtmenin en kolay yolu, güvenlik ilkesinden adlandırılmış bir izin kümesi alma yöntemidir.

Aşağıdaki yordam, yayımlanmış kodun yalnızca ortak türlerin ortak üyelerine erişebileceği test senaryoları için, kodunuzu kısmi güvenle çalıştıran bir korumalı uygulama etki alanı oluşturur. Sonraki yordamda, yayımlanmış kodun, eşit <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>veya daha az izin verilen derlemelerde ortak türlere ve üyelere erişebileceği test senaryolarına nasıl ekleneceğini gösterir.

#### <a name="to-create-an-application-domain-with-partial-trust"></a>Kısmi güvenle bir uygulama etki alanı oluşturmak için

1. Korumalı uygulama etki alanındaki derlemelere verilecek bir izin kümesi oluşturun. Bu durumda, Internet bölgesinin izin kümesi kullanılır.

    [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
    [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]

2. Uygulama etki <xref:System.AppDomainSetup> alanını bir uygulama yolu ile başlatmak için bir nesne oluşturun.

    > [!IMPORTANT]
    > Kolaylık olması için, bu kod örneği geçerli klasörü kullanır. Aslında Internet 'ten gelen kodu çalıştırmak için, güvenilir olmayan kod [için nasıl yapılır: Bir korumalı alanda](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)kısmen güvenilen kodu çalıştırın.

    [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
    [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]

3. Uygulama etki alanı kurulum bilgilerini ve uygulama etki alanında yürütülen tüm derlemeler için izin kümesini belirterek uygulama etki alanını oluşturun.

    [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
    [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]

    <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> Yöntem aşırı yüklemesinin son parametresi, uygulama etki alanının izin kümesi yerine, tam güven verilecek bir derleme kümesi belirtmenizi sağlar. Bu derlemeler genel derleme önbelleğinde olduğundan, uygulamanızın kullandığı .NET Framework derlemelerini belirtmeniz gerekmez. Genel derleme önbelleğindeki derlemeler her zaman tam olarak güvenilirdir. Bu parametreyi, genel derleme önbelleğinde olmayan tanımlayıcı adlandırılmış derlemeler belirtmek için kullanabilirsiniz.

### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Korumalı etki alanlarına Kısıttedmemberaccess ekleniyor

Konak uygulamalar, anonim olarak barındırılan dinamik yöntemlerin, kodu yayan derlemenin güven düzeyine eşit veya daha küçük olan derlemelerde bulunan özel verilere erişmelerine izin verebilir. Tam zamanında (JIT) görünürlük denetimlerini atlamak için bu kısıtlı özelliği etkinleştirmek üzere, ana bilgisayar uygulaması, izin kümesine <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> (RMA) bayrağını içeren bir nesne ekler.

Örneğin, bir ana bilgisayar Internet uygulamalarına Internet izinleri artı RMA verebilir, böylece bir Internet uygulaması kendi derlemelerindeki özel verilere erişen kodu yayabilir. Erişim, eşit veya daha az güven Derlemeleriyle sınırlı olduğundan, bir Internet uygulaması .NET Framework derlemeleri gibi tamamen güvenilen derlemelerin üyelerine erişemez.

> [!NOTE]
> Ayrıcalık yükseltmesini engellemek için, anonim olarak barındırılan dinamik yöntemler oluşturulduğunda, yayma derlemesi için yığın bilgileri dahil edilir. Yöntemi çağrıldığında, yığın bilgileri denetlenir. Bu nedenle, tam güvenilir koddan çağrılan, anonim olarak barındırılan bir dinamik yöntem hala yayma derlemesinin güven düzeyiyle sınırlıdır.

#### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Kısmi güven artı RMA ile bir uygulama etki alanı oluşturmak için

1. <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (RMA) <xref:System.Security.Permissions.ReflectionPermission>bayrağıylayeni bir nesne oluşturun ve izni izin kümesine eklemek için yönteminikullanın.<xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType>

    [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
    [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]

    <xref:System.Security.PermissionSet.AddPermission%2A> Yöntemi, zaten dahil değilse izin kümesine izin ekler. İzin verme kümesine zaten eklenirse, belirtilen bayraklar var olan izne eklenir.

    > [!NOTE]
    > RMA, anonim olarak barındırılan dinamik yöntemlerin bir özelliğidir. Sıradan dinamik yöntemler JıT görünürlük denetimlerini atlediğinde, oluşturulan kod tam güven gerektirir.

2. Uygulama etki alanı kurulum bilgilerini ve izin kümesini belirterek uygulama etki alanını oluşturun.

    [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
    [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]

<a name="Running_code"></a>

## <a name="running-code-in-sandboxed-application-domains"></a>Korumalı uygulama etki alanlarında kod çalıştırma

Aşağıdaki yordamda bir uygulama etki alanında yürütülebilecek Yöntemler, etki alanında sınıfın bir örneği oluşturma ve yöntemlerini yürütme yöntemleri kullanılarak bir sınıfın nasıl tanımlanacağı açıklanmaktadır.

#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Uygulama etki alanında bir yöntemi tanımlamak ve yürütmek için

1. Öğesinden <xref:System.MarshalByRefObject>türetilen bir sınıf tanımlayın. Bu, diğer uygulama etki alanlarında sınıfının örneklerini oluşturmanızı ve uygulama etki alanı sınırları arasında Yöntem çağrıları yapmanızı sağlar. Bu örnekteki sınıf adı `Worker`.

    [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
    [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]

2. Yürütmek istediğiniz kodu içeren bir genel yöntem tanımlayın. Bu örnekte, kod basit bir dinamik yöntem yayar, yöntemi yürütmek için bir temsilci oluşturur ve temsilciyi çağırır.

    [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
    [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]

3. Ana programınızda, derlemelerinizin görünen adını alın. Bu ad, korumalı uygulama etki alanında `Worker` sınıfının örneklerini oluşturduğunuzda kullanılır.

    [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
    [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]

4. Ana programınızda, Bu izlenecek yolda [ilk yordamda](#Setting_up) açıklandığı gibi bir korumalı uygulama etki alanı oluşturun. Yöntem yalnızca ortak Yöntemler kullandığından, `Internet` izin kümesine herhangi bir izin eklemeniz gerekmez. `SimpleEmitDemo`

5. Ana programınızda, korumalı uygulama etki alanında `Worker` sınıfının bir örneğini oluşturun.

    [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
    [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]

    <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Yöntemi, hedef uygulama etki alanında nesnesini oluşturur ve nesnenin özelliklerini ve yöntemlerini çağırmak için kullanılabilecek bir ara sunucu döndürür.

    > [!NOTE]
    > Bu kodu Visual Studio 'da kullanırsanız, sınıfının adını ad alanını içerecek şekilde değiştirmelisiniz. Varsayılan olarak, ad alanı projenin adıdır. Örneğin, proje "PartialTrust" ise, sınıf adının "PartialTrust. Worker" olması gerekir.

6. `SimpleEmitDemo` Yöntemi çağırmak için kod ekleyin. Çağrı, uygulama etki alanı sınırı üzerinden sıralanır ve kod, korumalı uygulama etki alanında yürütülür.

    [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
    [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]

<a name="Using_methods"></a>

## <a name="using-anonymously-hosted-dynamic-methods"></a>Anonim olarak barındırılan dinamik yöntemler kullanma

Anonim olarak barındırılan dinamik yöntemler, sistem tarafından sağlanmış bir saydam derleme ile ilişkilendirilir. Bu nedenle, içerdikleri kod saydamdır. Diğer yandan sıradan dinamik yöntemlerin, mevcut bir modülle ilişkilendirilmesi gerekir (doğrudan belirtilen veya bir ilişkili türden çıkarılan) ve güvenlik düzeyini bu modülden taşıyın.

> [!NOTE]
> Anonim barındırma sağlayan derleme ile dinamik bir yöntemi ilişkilendirmenin tek yolu, aşağıdaki yordamda açıklanan oluşturucuları kullanmaktır. Anonim barındırma derlemesinde açıkça bir modül belirtemezsiniz.

Sıradan dinamik yöntemler, ilişkili oldukları modülün iç üyelerine veya ilişkilendirildikleri türün özel üyelerine erişimi vardır. Anonim olarak barındırılan dinamik yöntemler diğer koddan yalıtılmış olduğundan, özel verilere erişimi yoktur. Ancak, özel verilere erişim kazanmak için JıT görünürlük denetimlerini atlayabilecekleri sınırlı bir özelliği vardır. Bu özellik, güven düzeylerine sahip olan ve kodu gösteren derlemenin güven düzeyinden daha küçük olan Derlemelerle sınırlıdır.

Ayrıcalık yükseltmesini engellemek için, anonim olarak barındırılan dinamik yöntemler oluşturulduğunda, yayma derlemesi için yığın bilgileri dahil edilir. Yöntemi çağrıldığında, yığın bilgileri denetlenir. Tam olarak güvenilen koddan çağrılan, anonim olarak barındırılan dinamik bir yöntem yine de onu yayılan derlemenin güven düzeyiyle sınırlıdır.

#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Anonim olarak barındırılan dinamik yöntemler kullanmak için

- İlişkili bir modül veya tür belirtmeyen bir Oluşturucu kullanarak anonim olarak barındırılan bir dinamik yöntem oluşturun.

  [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
  [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]

  Anonim olarak barındırılan dinamik bir yöntem yalnızca ortak türleri ve yöntemleri kullanıyorsa, kısıtlı üye erişimi gerektirmez ve JıT görünürlük denetimlerini atlamak zorunda kalmaz.

  Dinamik bir yöntemi yaymak için özel izin gerekmez, ancak bu kod, kullandığı türler ve yöntemler tarafından talep edilen izinleri gerektirir. Örneğin, oluşturulan kod bir dosyaya erişen bir yöntemi çağırırsa, bu gerektirir <xref:System.Security.Permissions.FileIOPermission>. Güven düzeyi bu izni içermiyorsa, oluşturulan kod yürütüldüğünde bir güvenlik özel durumu oluşturulur. Burada gösterilen kod yalnızca <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yöntemini kullanan dinamik bir yöntemi yayar. Bu nedenle, kod kısmen güvenilen konumlardan yürütülebilir.

- Alternatif olarak, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> oluşturucuyu kullanarak ve `restrictedSkipVisibility` parametresi için belirterek `true` , JIT görünürlük denetimlerini atlayabilme özelliğine sahip anonim olarak barındırılan bir dinamik yöntem oluşturun.

  [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
  [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]

  Kısıtlama, anonim olarak barındırılan dinamik yöntemin yalnızca güven düzeylerine sahip derlemelerdeki özel verilere, yayma derlemesinin güven düzeyine eşit veya ondan daha küçük bir erişim sağlayabilir. Örneğin, dinamik yöntem Internet güveni ile yürütülerek Internet güveni ile de yürütülen diğer derlemelerdeki özel verilere erişebilir, ancak .NET Framework derlemelerinin özel verilerine erişemez. .NET Framework derlemeleri genel bütünleştirilmiş kod önbelleğine yüklenir ve her zaman tam olarak güvenilirdir.

  Anonim olarak barındırılan dinamik yöntemler, JIT görünürlük denetimlerini atlamak için yalnızca ana bilgisayar uygulaması <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla izin veriyorsa bu kısıtlı özelliği kullanabilir. Bu izin talebi, yöntemi çağrıldığında yapılır.

  > [!NOTE]
  > Yayma derlemesi için çağrı yığını bilgileri, dinamik yöntem oluşturulduğunda dahil edilir. Bu nedenle talep, yöntemi çağıran derleme yerine yayma derlemesinin izinlerine göre yapılır. Bu, verilmiş kodun yükseltilmiş izinlerle yürütülmesini önler.

  Bu izlenecek yolun sonundaki [kod örneği](#Example) , kısıtlı üye erişiminin kullanımını ve sınırlamalarını gösterir. `Worker` Sınıfı, görünürlük denetimlerini atlayabilme özelliği olmadan veya olmadan anonim olarak barındırılan dinamik yöntemler oluşturabileceğiniz bir yöntemi içerir ve örnek, bu yöntemi farklı olan uygulama etki alanlarında yürütmenin sonucunu gösterir güven düzeyleri.

  > [!NOTE]
  > Görünürlük denetimlerini atlama yeteneği, anonim olarak barındırılan dinamik yöntemlerin bir özelliğidir. Sıradan dinamik yöntemler JıT görünürlük denetimlerini atlar, bunlara tam güven verilmelidir.

<a name="Example"></a>

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki kod örneği, anonim olarak barındırılan dinamik yöntemlerin <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> JIT görünürlük denetimlerini atlamasını sağlayan bayrağın kullanımını gösterir, ancak yalnızca hedef üye kodu yayan derlemeden daha eşit veya daha düşük bir güven düzeyindedir.

Örnek, uygulama etki `Worker` alanı sınırları genelinde sıralanabilen bir sınıfı tanımlar. Sınıfında dinamik yöntemler sunan `AccessPrivateMethod` ve yürütülen iki yöntem aşırı yüklemesi vardır. İlk aşırı yükleme, `PrivateMethod` `Worker` sınıfının özel yöntemini çağıran dinamik bir yöntemi yayar ve JIT görünürlük denetimleri olan veya olmayan dinamik yöntemi yayabilir. İkinci aşırı yükleme, `internal` <xref:System.String> sınıfının bir özelliğine (`Friend` Visual Basic özelliği) erişen dinamik bir yöntemi yayar.

Örnek, `Internet` izinlerle sınırlı bir izin kümesi oluşturmak için bir yardımcı yöntemi kullanır ve ardından, etki alanında çalışan tüm kodun bu izin kümesini <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> kullandığını belirtmek için yöntem aşırı yüklemesini kullanarak bir uygulama etki alanı oluşturur. Örnek, uygulama etki alanında `Worker` sınıfının bir örneğini oluşturur ve `AccessPrivateMethod` yöntemi iki kez yürütür.

- `AccessPrivateMethod` Yöntem ilk yürütüldüğünde JIT görünürlük denetimleri zorlanır. JıT görünürlük denetimleri özel yönteme erişmesini önleyebildiğinden, dinamik yöntem çağrıldığında başarısız olur.

- `AccessPrivateMethod` Yöntemi ikinci kez yürütüldüğünde JIT görünürlük denetimleri atlanır. Dinamik yöntem derlendiğinde başarısız olur, çünkü `Internet` izin kümesi görünürlük denetimlerini atlamak için yeterli izinleri vermez.

Örnek, ' <xref:System.Security.Permissions.ReflectionPermission> i <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> izin kümesine ekler. Örnek daha sonra ikinci bir etki alanı oluşturur ve etki alanında çalıştırılan tüm kodların yeni izin kümesindeki izinleri verildiğini belirtmek için kullanılır. Örnek, yeni uygulama etki alanında `Worker` sınıfının bir örneğini oluşturur ve `AccessPrivateMethod` yönteminin her iki yüklerini de yürütür.

- `AccessPrivateMethod` Metodun ilk aşırı yüklemesi yürütülür ve JIT görünürlük denetimleri atlanır. Kodu veren derleme özel yöntemi içeren derlemeyle aynı olduğundan, dinamik yöntem başarıyla derlenir ve yürütülür. Bu nedenle, güven düzeyleri eşittir. `Worker` Sınıfı içeren uygulama birden fazla derlemeye sahipse, aynı işlem bu derlemelerin herhangi biri için başarılı olur, çünkü hepsi aynı güven düzeyinde olacaktır.

- `AccessPrivateMethod` Metodun ikinci aşırı yüklemesi yürütülür ve daha sonra JIT görünürlük denetimleri atlanır. Bu kez, `internal` <xref:System.String> sınıfının `FirstChar` özelliğine erişmeye çalıştığı için dinamik yöntem derlendiğinde başarısız olur. <xref:System.String> Sınıfını içeren derleme tam olarak güvenilirdir. Bu nedenle, kodu yayan derlemeden daha yüksek bir güven düzeyindedir.

Bu karşılaştırma <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> , kısmen güvenilen kodun, güvenilen kodun güvenliği tehlikeye atmadan diğer kısmen güvenilen kod için görünürlük denetimlerini atlamasını sağlar.

### <a name="code"></a>Kod

[!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
[!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]

## <a name="compiling-the-code"></a>Kod Derleniyor

- Visual Studio 'da Bu kod örneğini oluşturursanız, <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> yöntemine geçirdiğinizde sınıfının adını ad alanını içerecek şekilde değiştirmelisiniz. Varsayılan olarak, ad alanı projenin adıdır. Örneğin, proje "PartialTrust" ise, sınıf adının "PartialTrust. Worker" olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Yaymadaki Güvenlik Sorunları](security-issues-in-reflection-emit.md)
- [Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır](../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
