---
title: Kurumsal Hizmetler ve COM+ İşlemleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
ms.openlocfilehash: 98890c4c054a5063f91e429b13cfd6bab9f3dc15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596866"
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Kurumsal Hizmetler ve COM+ İşlemleri ile Birlikte Çalışabilirlik
<xref:System.Transactions> Ad alanı, bu ad alanı kullanılarak oluşturulan işlem nesneleri ve COM + oluşturulan işlemleri arasındaki birlikte çalışabilirlik destekler.  
  
 Kullanabilirsiniz <xref:System.Transactions.EnterpriseServicesInteropOption> , yeni bir oluşturduğunuzda numaralandırma <xref:System.Transactions.TransactionScope> COM + ile birlikte çalışabilirlik düzeyini belirtmek için örneği.  
  
 Varsayılan olarak uygulama kodunuz statik ettiğinde <xref:System.Transactions.Transaction.Current%2A> özelliği <xref:System.Transactions> için geçerli değilse, bir işlem aramaya denemeleri veya bir <xref:System.Transactions.TransactionScope> , belirleyen nesne <xref:System.Transactions.Transaction.Current%2A> olduğu **null**. Bunlardan herhangi birini bulamazsa <xref:System.Transactions> COM + bağlamı için bir işlem sorgular. Rağmen dikkat edin <xref:System.Transactions> bir işlem bulabilirsiniz COM + bağlamdan, yine de yerel işlemler yakın düzenin bulunmasını <xref:System.Transactions>.  
  
## <a name="interoperability-levels"></a>Birlikte çalışabilirlik düzeyleri  
 <xref:System.Transactions.EnterpriseServicesInteropOption> Numaralandırma aşağıdaki birlikte çalışabilirlik düzeyleri tanımlar —<xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 <xref:System.Transactions.TransactionScope> Sınıfı sağlar kabul oluşturucular <xref:System.Transactions.EnterpriseServicesInteropOption> bir parametre olarak.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>, hiçbir birlikte çalışabilirlik olduğunu adı gelir gibi anlamına gelir <xref:System.EnterpriseServices> bağlamları ve işlem kapsamları. Oluşturduktan sonra bir <xref:System.Transactions.TransactionScope> nesnesi ile <xref:System.Transactions.EnterpriseServicesInteropOption.None>, herhangi bir değişiklik <xref:System.Transactions.Transaction.Current%2A> COM + bağlamında yansıtılmaz. Benzer şekilde, COM + bağlamında işlem değişiklikler yansıtılmaz <xref:System.Transactions.Transaction.Current%2A>. Bu işlem için en hızlı moddur <xref:System.Transactions> gereken ek eşitleme olduğundan. <xref:System.Transactions.EnterpriseServicesInteropOption.None> tarafından kullanılan varsayılan değer <xref:System.Transactions.TransactionScope> kabul ediyor musunuz tüm oluşturucular ile <xref:System.Transactions.EnterpriseServicesInteropOption> bir parametre olarak.  
  
 Birleştirmek isterseniz <xref:System.EnterpriseServices> ortam işleminizin ile işlemleri, ihtiyacınız ya da kullanılacak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> veya <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Bu değerleri her ikisi de Hizmetleri bileşenleri olmadan denilen bir özelliği kullanır ve bu nedenle, Windows XP Service Pack 2 veya Windows Server 2003 üzerinde bunları kullanırken çalışıyor olması gerekir.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> belirtir ortam işlemleri için <xref:System.Transactions> ve <xref:System.EnterpriseServices> her zaman aynıdır. Yeni bir oluşturma sonuçlarını <xref:System.EnterpriseServices> işlem bağlamını ve uygulama için geçerli olan işlem <xref:System.Transactions.TransactionScope> bu bağlamı için geçerli olacak. Gibi işlemde olarak <xref:System.Transactions.Transaction.Current%2A> işlem sırasında ile eşitleme tamamen yer <xref:System.EnterpriseServices.ContextUtil.Transaction%2A>. Bu değer, oluşturulacak yeni COM + bağlamları gerekebileceğinden performans cezası tanıtır.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>aşağıdaki gereksinimleri belirtir.  
  
- Zaman <xref:System.Transactions.Transaction.Current%2A> tabanlıysa <xref:System.Transactions> işlemleri varsayılan bağlamı dışındaki bir bağlamda çalışır olduğunu algılarsa COM + bağlamında desteklemelidir. Not varsayılan bağlamı bir işlem içeremez. Varsayılan bağlamında, bu nedenle, hatta ile <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, tarafından kullanılan iş parçacığı yerel depolama alanında depolanan işlem <xref:System.Transactions> için döndürülen <xref:System.Transactions.Transaction.Current%2A>.  
  
- Yeni bir <xref:System.Transactions.TransactionScope> nesnesi oluşturulur ve varsayılan bağlamı için geçerli olan işlem dışındaki bir bağlamda oluşturulmasıyla meydana <xref:System.Transactions.TransactionScope> nesne yansıtılan COM +. Bu durumda, <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> gibi davranır <xref:System.Transactions.EnterpriseServicesInteropOption.Full> , yeni bir COM + içeriği oluşturur.  
  
 Ayrıca, <xref:System.Transactions.Transaction.Current%2A> her ikisini de ayarlanmış <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ve <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, her iki mod yaptığından <xref:System.Transactions.Transaction.Current%2A> doğrudan ayarlanamaz.  Ayarlanacak yapmaya <xref:System.Transactions.Transaction.Current%2A> doğrudan dışındaki oluşturma bir <xref:System.Transactions.TransactionScope> sonuçlanır bir <xref:System.InvalidOperationException>. <xref:System.Transactions.EnterpriseServicesInteropOption> Numaralandırma değeri kullanmak üzere hangi değeri açıkça belirtmeyen yeni işlem kapsamlar tarafından devralınır. Yeni bir oluşturursanız, örneğin, <xref:System.Transactions.TransactionScope> nesnesi ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full>ve sonra bir saniye oluşturun <xref:System.Transactions.TransactionScope> nesnesi ancak belirtmeyin bir <xref:System.Transactions.EnterpriseServicesInteropOption> değeri, ikinci <xref:System.Transactions.TransactionScope> nesne de sahip bir <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.  
  
 Özet olarak, yeni bir işlem kapsam oluştururken aşağıdaki kurallar geçerlidir:  
  
1. <xref:System.Transactions.Transaction.Current%2A> bir işlem olup olmadığını görmek için denetlenir. Bu onay sonuçlanır:  
  
    - Bir kapsam olup olmadığını denetleyin.  
  
    - Değerini bir kapsam ise <xref:System.Transactions.EnterpriseServicesInteropOption> kapsam başlangıçta oluşturulduğunda geçirilen numaralandırma denetlenir.  
  
    - Varsa <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırma ayarı <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, COM + işlem (<xref:System.EnterpriseServices> işlem) öncelikli <xref:System.Transactions> işlem yönetilen iş parçacığı yerel depolama.  
  
         Değer ayarlanmışsa <xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions> işlem yönetilen iş parçacığı yerel depolama alanında öncelik alır.  
  
         Değer ise <xref:System.Transactions.EnterpriseServicesInteropOption.Full>bir COM + işlem olduğu ve yalnızca bir işlem yok.  
  
2. Değerini <xref:System.Transactions.TransactionScopeOption> içindeki numaralandırma geçirilen <xref:System.Transactions.TransactionScope> Oluşturucu denetlenir. Bu, yeni bir işlem oluşturulmuş olmadığını belirler.  
  
3. Yeni bir işlem oluşturulur için aşağıdaki değerleri arasında olup olmadığını <xref:System.Transactions.EnterpriseServicesInteropOption> neden:  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Full>: bir COM + bağlamla ilişkili bir işlem oluşturulur.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.None>: bir <xref:System.Transactions> işlem oluşturulur.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>: bir COM + bağlamı ise, bir işlem oluşturulur ve bağlamına iliştirilemez.  
  
 Aşağıdaki tabloda Enterprise Hizmetleri (ES) bağlamını ve kullanarak bir işlem gerektiren bir işlem kapsamı gösterilmektedir <xref:System.Transactions.EnterpriseServicesInteropOption> sabit listesi.  
  
|ES bağlamı|Yok.|Otomatik|Tam|  
|----------------|----------|---------------|----------|  
|Varsayılan bağlamı|Varsayılan bağlamı|Varsayılan bağlamı|Yeni Oluştur <br />işlem bağlamı|  
|Varsayılan olmayan bağlamı|İstemcinin içeriği|Yeni bir işlem bağlam oluşturur|Yeni bir işlem bağlam oluşturur|  
  
 Aşağıdaki tabloda ortam işlem, belirli bir nedir gösterilmektedir <xref:System.EnterpriseServices> bağlamını ve kullanarak bir işlem gerektiren bir işlem kapsamı <xref:System.Transactions.EnterpriseServicesInteropOption> sabit listesi.  
  
|ES bağlamı|Yok.|Otomatik|Tam|  
|----------------|----------|---------------|----------|  
|Varsayılan bağlamı|ST|ST|ES|  
|Varsayılan olmayan bağlamı|ST|ES|ES|  
  
 Yukarıdaki tabloda:  
  
- ST anlamına gelir kapsamın ortam işlem tarafından yönetilir <xref:System.Transactions>herhangi ayrı <xref:System.EnterpriseServices> bulunabilecek bağlamı'nın işlem.  
  
- ES anlamına gelir kapsamın ortam işlem aynı olduğunu <xref:System.EnterpriseServices> bağlamı'nın işlem.
