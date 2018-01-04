---
title: "Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 246658ceb2fdbaa302753441ca5e34a1eef92b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik
<xref:System.Transactions> Ad alanı bu ad alanı kullanılarak oluşturulan işlem nesneler ile oluşturulan COM + işlemleri arasında birlikte çalışabilirlik destekler.  
  
 Kullanabilirsiniz <xref:System.Transactions.EnterpriseServicesInteropOption> , yeni bir oluşturduğunuzda numaralandırma <xref:System.Transactions.TransactionScope> COM + ile birlikte çalışabilirlik düzeyini belirtmek için örneği.  
  
 Varsayılan olarak, uygulama kodunuzun statik denetlediğinde, <xref:System.Transactions.Transaction.Current%2A> özelliği, <xref:System.Transactions> , aksi takdirde geçerli bir işlem için Ara girişimleri veya <xref:System.Transactions.TransactionScope> , belirleyen nesne <xref:System.Transactions.Transaction.Current%2A> olan **null**. Bunlar, birini bulamazsanız <xref:System.Transactions> COM + bağlamı bir işlem için sorgular. Unutmayın <xref:System.Transactions> bir işlem bulabilirsiniz COM + bağlamdan bunu hala yerel işlemler çalışmak <xref:System.Transactions>.  
  
## <a name="interoperability-levels"></a>Birlikte çalışabilirlik düzeyleri  
 <xref:System.Transactions.EnterpriseServicesInteropOption> Numaralandırma aşağıdaki birlikte çalışabilirlik düzeyleri tanımlar —<xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 <xref:System.Transactions.TransactionScope> SAX kabul oluşturucular <xref:System.Transactions.EnterpriseServicesInteropOption> bir parametre olarak.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>, adından da anlaşılacağı gibi hiçbir işlerliği olduğu anlamına gelir <xref:System.EnterpriseServices> bağlamları ve işlem kapsamları. Oluşturduktan sonra bir <xref:System.Transactions.TransactionScope> nesnesi ile <xref:System.Transactions.EnterpriseServicesInteropOption.None>, herhangi bir değişiklik <xref:System.Transactions.Transaction.Current%2A> COM + bağlamında yansıtılmaz. Benzer şekilde, COM + içeriği işlemde değişiklikler yansıtılmaz <xref:System.Transactions.Transaction.Current%2A>. Bu işlem için en hızlı moddur <xref:System.Transactions> olduğu için hiçbir ek eşitlemesi gerekiyor. <xref:System.Transactions.EnterpriseServicesInteropOption.None>tarafından kullanılan varsayılan değer <xref:System.Transactions.TransactionScope> kabul tüm oluşturucular ile <xref:System.Transactions.EnterpriseServicesInteropOption> bir parametre olarak.  
  
 Birleştirmek istiyorsanız, <xref:System.EnterpriseServices> ortam işleminiz işlemleri, gereken kullanın ya da <xref:System.Transactions.EnterpriseServicesInteropOption.Full> veya <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Bu değerleri her ikisi de Hizmetleri bileşenleri olmadan denilen bir özelliği kullanır ve bu nedenle, Windows XP Service Pack 2 veya Windows Server 2003 üzerinde bunları kullanırken çalışıyor olması gerekir.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>belirleyen ortam işlemleri için <xref:System.Transactions> ve <xref:System.EnterpriseServices> her zaman aynıdır. Yeni bir oluşturmada sonuçları <xref:System.EnterpriseServices> işlem bağlamını ve uygulama için geçerli olan işlem <xref:System.Transactions.TransactionScope> bu bağlam için geçerli olacak. Şekilde hareket <xref:System.Transactions.Transaction.Current%2A> işlemde eşitlemede tamamen yer <xref:System.EnterpriseServices.ContextUtil.Transaction%2A>. Oluşturulacak yeni COM + bağlamları gerektiğinden bu değer bir performans cezası tanıtır.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>aşağıdaki gereksinimleri belirtir.  
  
-   Zaman <xref:System.Transactions.Transaction.Current%2A> denetlenir, <xref:System.Transactions> varsayılan bağlamı farklı bir bağlam içinde çalıştığını algılarsa işlemleri COM + bağlamda desteklemelidir. Varsayılan bağlamı bir işlem içeremez unutmayın. Bu nedenle, varsayılan bağlamında bile ile <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, tarafından kullanılan iş parçacığı yerel depolaması depolanan işlem <xref:System.Transactions> için döndürülen <xref:System.Transactions.Transaction.Current%2A>.  
  
-   Yeni <xref:System.Transactions.TransactionScope> nesnesi oluşturulur ve varsayılan bağlam için geçerli olan işlem farklı bir bağlam oluşturma oluşuyor <xref:System.Transactions.TransactionScope> nesne yansıtılan COM +. Bu durumda, <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> gibi davranır <xref:System.Transactions.EnterpriseServicesInteropOption.Full> , yeni bir COM + içeriği oluşturur.  
  
 Ayrıca, <xref:System.Transactions.Transaction.Current%2A> her ikisini de ayarlanmış <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, her iki mod yaptığından <xref:System.Transactions.Transaction.Current%2A> doğrudan ayarlanamaz.  Ayarlanacak yapmaya <xref:System.Transactions.Transaction.Current%2A> doğrudan dışındaki oluşturma bir <xref:System.Transactions.TransactionScope> sonuçlanır bir <xref:System.InvalidOperationException>. <xref:System.Transactions.EnterpriseServicesInteropOption> Numaralandırma değeri açıkça kullanmak için hangi değer belirtmeyin yeni işlem kapsamlar tarafından devralınır. Yeni bir oluşturursanız, örneğin, <xref:System.Transactions.TransactionScope> nesnesi ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full>ve sonra bir saniye oluşturun <xref:System.Transactions.TransactionScope> nesnesi ancak belirtmeyin bir <xref:System.Transactions.EnterpriseServicesInteropOption> değeri, ikinci <xref:System.Transactions.TransactionScope> nesne de sahip bir <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.  
  
 Özet olarak, yeni bir işlem kapsamı oluştururken aşağıdaki kurallar geçerli olur:  
  
1.  <xref:System.Transactions.Transaction.Current%2A>bir işlem olup olmadığını görmek için denetlenir. Bu onay sonuçlanır:  
  
    -   Bir kapsam olup olmadığını denetleyin.  
  
    -   Değerini bir kapsam ise <xref:System.Transactions.EnterpriseServicesInteropOption> kapsam başlangıçta oluşturulduğunda geçirilen numaralandırma denetlenir.  
  
    -   Varsa <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırma ayarlanmış <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, COM + işlem (<xref:System.EnterpriseServices> hareket) önceliklidir <xref:System.Transactions> yönetilen iş parçacığı yerel depolaması işlemde.  
  
         Değer ayarlanmışsa <xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions> yönetilen iş parçacığı yerel depolaması işlemde önceliklidir.  
  
         Değer ise <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, yalnızca bir işlem yok ve bir COM + işlem değil.  
  
2.  Değeri <xref:System.Transactions.TransactionScopeOption> numaralandırması geçirilen <xref:System.Transactions.TransactionScope> Oluşturucusu denetlenir. Bu, yeni bir işlem oluşturulmuş olmadığını belirler.  
  
3.  Yeni bir işlem oluşturulmuş olması için aşağıdaki değerleri arasında olup olmadığını <xref:System.Transactions.EnterpriseServicesInteropOption> neden:  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.Full>: COM + bağlamla ilişkili bir işlem oluşturulur.  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.None>: bir <xref:System.Transactions> işlem oluşturulur.  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>: bir COM + bağlamı ise, bir işlem oluşturulur ve bağlamına bağlı.  
  
 Kurumsal Hizmetler (ES) bağlamını ve kullanarak bir işlem gerektiren bir işlem kapsamı aşağıdaki tabloda gösterilmektedir <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırması.  
  
|ES bağlamı|Hiçbiri|Otomatik|Tam|  
|----------------|----------|---------------|----------|  
|Varsayılan bağlamı|Varsayılan bağlamı|Varsayılan bağlamı|Yeni Oluştur <br />işlem bağlamı|  
|Varsayılan olmayan bağlamı|İstemcinin içeriği|Yeni işlem bağlamı oluşturma|Yeni işlem bağlamı oluşturma|  
  
 Aşağıdaki tabloda ortam işlem, belirli bir nedir gösterilmektedir <xref:System.EnterpriseServices> bağlamını ve kullanarak bir işlem gerektiren bir işlem kapsamı <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırması.  
  
|ES bağlamı|Hiçbiri|Otomatik|Tam|  
|----------------|----------|---------------|----------|  
|Varsayılan bağlamı|ST|ST|ES|  
|Varsayılan olmayan bağlamı|ST|ES|ES|  
  
 Yukarıdaki tabloda:  
  
-   ST anlamına gelir kapsamın ortam işlem yöneten <xref:System.Transactions>tümünden ayrı <xref:System.EnterpriseServices> bulunabilecek bağlamın işlem.  
  
-   ES anlamına gelir kapsamın ortam işlem aynı olduğunu <xref:System.EnterpriseServices> bağlamın işlem.
