---
title: Kurumsal Hizmetler ve COM+ İşlemleri ile Birlikte Çalışabilirlik
description: System. Transactions ad alanını kullanarak .NET 'teki kurumsal hizmetler ve COM+ işlemleri ile birlikte çalışabilirliği anlayın.
ms.date: 03/30/2017
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
ms.openlocfilehash: 48cb006a4294b7c43de262eb2d19c6c4ea9d22fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186776"
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Kurumsal Hizmetler ve COM+ İşlemleri ile Birlikte Çalışabilirlik

<xref:System.Transactions>Ad alanı, bu ad alanı ve com+ aracılığıyla oluşturulan işlemler kullanılarak oluşturulan işlem nesneleri arasında birlikte çalışabilirliği destekler.  
  
 Kullanabilirsiniz <xref:System.Transactions.EnterpriseServicesInteropOption> , yeni bir oluşturduğunuzda numaralandırma <xref:System.Transactions.TransactionScope> COM + ile birlikte çalışabilirlik düzeyini belirtmek için örneği.  
  
 Varsayılan olarak, uygulama kodunuz statik özelliği denetlediğinde <xref:System.Transactions.Transaction.Current%2A> , <xref:System.Transactions> başka bir şekilde geçerli olan bir işlemi aramaya çalışır veya bunu belirleyen bir <xref:System.Transactions.TransactionScope> nesne <xref:System.Transactions.Transaction.Current%2A> **null**olduğunu belirler. Bunlardan birini bulamazsa, <xref:System.Transactions> bir işlem IÇIN com+ bağlamını sorgular. <xref:System.Transactions>Com+ bağlamından bir işlem bulabilse de, yerel olan işlemleri hala tercih eder <xref:System.Transactions> .  
  
## <a name="interoperability-levels"></a>Birlikte çalışabilirlik düzeyleri  

 <xref:System.Transactions.EnterpriseServicesInteropOption> Numaralandırma aşağıdaki birlikte çalışabilirlik düzeyleri tanımlar —<xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 <xref:System.Transactions.TransactionScope>Sınıfı bir parametre olarak kabul eden oluşturucular sağlar <xref:System.Transactions.EnterpriseServicesInteropOption> .  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>Adından da anlaşılacağı gibi, <xref:System.EnterpriseServices> bağlamlar ve işlem kapsamları arasında birlikte çalışabilirlik olmadığını gösterir. Oluşturduktan sonra bir <xref:System.Transactions.TransactionScope> nesnesi ile <xref:System.Transactions.EnterpriseServicesInteropOption.None>, herhangi bir değişiklik <xref:System.Transactions.Transaction.Current%2A> COM + bağlamında yansıtılmaz. Benzer şekilde, COM+ bağlamındaki işlemde yapılan değişiklikler ' de yansıtılmaz <xref:System.Transactions.Transaction.Current%2A> . Bu, gerekli ek eşitleme olmadığından, için en hızlı işlem modudur <xref:System.Transactions> . <xref:System.Transactions.EnterpriseServicesInteropOption.None> , <xref:System.Transactions.TransactionScope> parametresi olarak kabul etmayan tüm oluşturucularla tarafından kullanılan varsayılan değerdir <xref:System.Transactions.EnterpriseServicesInteropOption> .  
  
 <xref:System.EnterpriseServices>İşlemleri çevresel işlem ile birleştirmek istiyorsanız, veya kullanmanız gerekir <xref:System.Transactions.EnterpriseServicesInteropOption.Full> <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> . Bu değerleri her ikisi de Hizmetleri bileşenleri olmadan denilen bir özelliği kullanır ve bu nedenle, Windows XP Service Pack 2 veya Windows Server 2003 üzerinde bunları kullanırken çalışıyor olması gerekir.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve için çevresel işlemlerin <xref:System.Transactions> <xref:System.EnterpriseServices> her zaman aynı olduğunu belirtir. Yeni bir <xref:System.EnterpriseServices> İşlemsel bağlam oluşturulmasına ve bu bağlamda geçerli olması için geçerli olan işlemin uygulanmasına neden olur <xref:System.Transactions.TransactionScope> . Bu nedenle, içindeki işlem <xref:System.Transactions.Transaction.Current%2A> içindeki işlemle tamamen eşitleme yapılır <xref:System.EnterpriseServices.ContextUtil.Transaction%2A> . Bu değer, yeni COM+ bağlamlarının oluşturulması gerekebilecek için bir performans cezası sunar.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>aşağıdaki gereksinimleri belirtir.  
  
- <xref:System.Transactions.Transaction.Current%2A>İşaretlendiğinde, <xref:System.Transactions> varsayılan bağlamdan farklı bir bağlamda ÇALıŞTıĞıNı algılarsa com+ bağlamındaki işlemleri desteklemelidir. Varsayılan bağlamın bir işlem içeremediğini unutmayın. Bu nedenle, varsayılan bağlamda ile birlikte <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> , tarafından kullanılan iş parçacığı yerel depolama alanında depolanan işlem <xref:System.Transactions> için döndürülür <xref:System.Transactions.Transaction.Current%2A> .  
  
- Yeni bir <xref:System.Transactions.TransactionScope> nesne oluşturulduysa ve oluşturma varsayılan bağlam dışında bir bağlamda oluşursa, nesne için geçerli olan Işlem <xref:System.Transactions.TransactionScope> com+ ' a yansıtılmalıdır. Bu durumda, <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> gibi davranır <xref:System.Transactions.EnterpriseServicesInteropOption.Full> , yeni bir COM + içeriği oluşturur.  
  
 Ayrıca, <xref:System.Transactions.Transaction.Current%2A> her ikisini de ayarlanmış <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, her iki mod yaptığından <xref:System.Transactions.Transaction.Current%2A> doğrudan ayarlanamaz.  Ayarlanacak yapmaya <xref:System.Transactions.Transaction.Current%2A> doğrudan dışındaki oluşturma bir <xref:System.Transactions.TransactionScope> sonuçlanır bir <xref:System.InvalidOperationException>. <xref:System.Transactions.EnterpriseServicesInteropOption>Sabit listesi değeri, hangi değerin kullanılacağını açıkça belirtmeyen yeni işlem kapsamları tarafından devralınır. Yeni bir oluşturursanız, örneğin, <xref:System.Transactions.TransactionScope> nesnesi ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full>ve sonra bir saniye oluşturun <xref:System.Transactions.TransactionScope> nesnesi ancak belirtmeyin bir <xref:System.Transactions.EnterpriseServicesInteropOption> değeri, ikinci <xref:System.Transactions.TransactionScope> nesne de sahip bir <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.  
  
 Özet bölümünde, yeni bir işlem kapsamı oluştururken aşağıdaki kurallar geçerlidir:  
  
1. <xref:System.Transactions.Transaction.Current%2A> bir işlem olup olmadığını görmek için denetlenir. Bu onay sonuçlanır:  
  
    - Bir kapsam olup olmadığını denetleyin.  
  
    - Değerini bir kapsam ise <xref:System.Transactions.EnterpriseServicesInteropOption> kapsam başlangıçta oluşturulduğunda geçirilen numaralandırma denetlenir.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption>Sabit listesi olarak ayarlanırsa <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> , com+ işlemi ( <xref:System.EnterpriseServices> işlem) <xref:System.Transactions> yönetilen iş parçacığı yerel depolama alanındaki işlemden önceliklidir.  
  
         Değer olarak ayarlanırsa <xref:System.Transactions.EnterpriseServicesInteropOption.None> , <xref:System.Transactions> yönetilen iş parçacığı yerel depolama alanındaki işlem önceliklidir.  
  
         Değer ise <xref:System.Transactions.EnterpriseServicesInteropOption.Full> , yalnızca bir işlem vardır ve bu BIR com+ hareketinden biridir.  
  
2. <xref:System.Transactions.TransactionScopeOption>Oluşturucu tarafından geçirilen numaralandırmanın değeri <xref:System.Transactions.TransactionScope> denetlenir. Bu, yeni bir işlemin oluşturulması gerektiğini belirler.  
  
3. Yeni bir işlem oluşturulabileceğinden, aşağıdaki değerleri ile <xref:System.Transactions.EnterpriseServicesInteropOption> sonuçlanır:  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Full>: bir COM+ bağlamı ile ilişkili bir işlem oluşturulur.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.None>: bir <xref:System.Transactions> işlem oluşturulur.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>: bir COM+ bağlamı varsa, bir işlem oluşturulur ve içeriğe iliştirilir.  
  
 Aşağıdaki tabloda Enterprise Services (ES) bağlamı ve sabit listesini kullanarak bir işlem gerektiren bir işlem kapsamı gösterilmektedir <xref:System.Transactions.EnterpriseServicesInteropOption> .  
  
|ES bağlamı|Yok|Automatic|Tam|  
|----------------|----------|---------------|----------|  
|Varsayılan bağlamı|Varsayılan bağlamı|Varsayılan bağlamı|Yeni oluştur <br />işlem bağlamı|  
|Varsayılan olmayan bağlamı|İstemcinin içeriği|Yeni işlem temelli bağlam oluştur|Yeni işlem temelli bağlam oluştur|  
  
 Aşağıdaki tablo, ortam işleminin ne olduğunu, belirli bir <xref:System.EnterpriseServices> bağlam verildiğini ve sabit listesini kullanarak bir işlem gerektiren bir işlem kapsamını gösterir <xref:System.Transactions.EnterpriseServicesInteropOption> .  
  
|ES bağlamı|Yok|Automatic|Tam|  
|----------------|----------|---------------|----------|  
|Varsayılan bağlamı|ST|ST|ES|  
|Varsayılan olmayan bağlamı|ST|ES|ES|  
  
 Yukarıdaki tabloda:  
  
- ST, kapsamın çevresel işleminin tarafından yönetildiği <xref:System.Transactions> , herhangi bir bağlamın mevcut olabilecek herhangi bir işlemden ayrı olduğu anlamına gelir <xref:System.EnterpriseServices> .  
  
- ES, kapsamın çevresel işleminin bağlam hareketiyle aynı olduğu anlamına gelir <xref:System.EnterpriseServices> .
