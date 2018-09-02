---
title: İlke ile sipariş işleme
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: b927d8e7090f96b22c0510f9651070ab999c91be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398376"
---
# <a name="order-processing-with-policy"></a>İlke ile sipariş işleme
Sipariş işleme ilkesi örnek sunulan önemli özelliklerinden bazıları gösterilmektedir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF). Aşağıdaki işlevleri WF kurallar altyapısı için yenidir:  
  
-   İşleç aşırı yüklemesi için destek.  
  
-   Destek `new` vererek yeni nesneler ve diziler WF kuralları oluşturmak işleç.  
  
-   Kullanıcı deneyimini WF kurallardan genişletme yöntemlerini çağırma kodlama stilleri ile C# uyumlu hale getirmek genişletme yöntemleri için destek.  
  
> [!NOTE]
>  Bu örnek gerektiren [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] derlemek ve çalıştırmak için yüklenir. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Proje ve çözüm dosyaları açmak için gereklidir.  
  
 Örnek gösterir bir `OrderProcessingPolicy` proje numaralandırılmış bir kullanılabilir öğeleri ve bir posta kodu listesinden oluşur, bir müşteri sipariş girilir. İki girişin doğruysa sipariş başarıyla işlendi; Aksi takdirde, ilkeyi kullanan aşırı yüklenmiş bir hata nesneleri oluşturur `+` işleci ve önceden tanımlanmış bir uzantı yöntemi hataları kullanıcıyı bilgilendirmek üzere.  
  
> [!NOTE]
>  Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [C# sürüm 3.0 belirtimi](https://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Örnek, aşağıdaki projelerin oluşur:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` Tanımlayan bir sınıf kitaplığı `OrderError` ve `OrderErrorCollection` sınıfları. Bir `OrderError` Geçersiz girdi girildiğinde örneği oluşturulur. Kitaplık ayrıca bir genişletme yöntemi sağlar `OrderErrorCollection` veren sınıf `ErrorText` tüm özellik `OrderError` nesneler `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` Projedir tanımlayan tek bir konsol uygulaması WF `PolicyFromFile` etkinlik. Etkinlik aşağıdaki kurallar içerir:  
  
    -   `invalidItemNum`  
  
         Bu kural, öğe sayısı 1 ile 6, kapsamlı arasında olduğunu doğrular. Öğe numarası geçerli aralıkta ise, kural (konsola yazdırma dışında) bir şey yapmaz. Öğe sayısı 1 ile 6 değilse `invalidItemNum` kural şunları yapar:  
  
        1.  Yeni bir oluşturur `OrderError` maddeye geçirerek girilen ve ayarlar nesnesi `ErrorText` ve `CustomerName` nesnesindeki özellikleri.  
  
        2.  Oluşturur bir `invalidItemNumErrorCollection` nesne.  
  
        3.  Yeni oluşturulan ekler `OrderError` için örnek `invalidItemNumErrorCollection`.  
  
         Bu desteğini gösterir `new` ile örneği kuralları içindeki nesnelerinin işleci.  
  
    -   `invalidZip`  
  
         Bu kural, posta kodu 5 basamak bulunur ve bir aralıkta için 600 99998 doğrular. Posta kodu geçerli aralığında ise, kural (konsola yazdırma dışında) bir şey yapmaz. Posta kodu uzunluğu 5'ten veya posta kodu, 99998 00600 arasında değil, `invalidZip` kural şunları yapar:  
  
        1.  Oluşturur bir `OrderError` nesne, posta kodu girildi, geçirme ve ayarlar `ErrorText` ve `CustomerName` nesnesindeki özellikleri.  
  
        2.  Oluşturur bir `invalidZipCodeErrorCollection` nesne.  
  
        3.  Yeni oluşturulan ekler `OrderError` yeni oluşturulan örneğine `invalidZipCodeErrorCollection`.  
  
         Bu kural yeniden desteği gösterir `new` kuralları içindeki nesneleri somutlaştırmak olanak tanıyan işleci.  
  
    -   `displayErrors`  
  
         Bu kural, iki önceki iki kural tarafından eklenen herhangi bir hata olup olmadığını görmek için denetler `OrderErrorCollection` nesneleri `invalidItemNumErrorCollection` ve `invalidIZipCodeErrorCollection`. Hatalar varsa (ya da `invalidItemNumErrorCollection` veya `invalidZipCodeErrorCollection` değil `null`), kural şunları yapar:  
  
        1.  Aşırı yüklenen çağırır `+` içeriğinin kopyalanacağı işleci `invalidItemNumErrorCollection` ve `invalidZipCodeErrorCollection` için bir `invalidOrdersCollection``OrderErrorCollection` örneği.  
  
        2.  Çağrıları `PrintOrderErrors` genişletme yöntemini `invalidOrdersCollection` ve çıkaran `ErrorText` tüm özellik `orderError` nesneler `invalidOrdersCollection`.  
  
 Aşırı yüklenmiş işleç `+` üzerinde `OrderErrorCollection` tanımlanan `OrderErrorCollection` içinde sınıf `OrderErrorLibrary` proje. İki alan `OrderErrorCollection` nesneleri ve bunları birine birleştirir `OrderErrorCollection` nesne.  
  
 `PrintOrderErrors` Uzantı yönteminin tanımlandığı ayrıca `OrderErrorLibrary` proje. Uzantı, geliştiricilerin yeni yöntemler, bir sınıf türetmeniz ya da özgün türü yeniden derlemenize gerek kalmadan var olan bir CLR türünün ortak bir sözleşme eklemelerini sağlayan yeni bir C# özelliği yöntemlerdir.  
  
 Örneği çalıştırdığında bir ad, satın alınması öğesi öğe sayısını ve posta kodu girmeniz istenir. Bu bilgiler daha sonra ilke etkinliğinde tanımlanan kuralları tarafından doğrulanır. Programdan alınan çıkış örnek verilmiştir.  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  OrderProcessingPolicy.sln proje dosyasında açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümde iki farklı proje vardır: `OrderErrorLibrary` ve `OrderProcessingPolicy`. `OrderProcessingPolicy` Kullanan proje sınıfları ve yöntemleri tanımlanan `OrderErrorLibrary`.  
  
3.  Tüm projeler oluşturun.  
  
4.  **Çalıştır**'ı tıklayın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`