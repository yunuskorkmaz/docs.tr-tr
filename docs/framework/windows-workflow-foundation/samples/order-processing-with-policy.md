---
title: İlke ile işlem sırası
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f99db44a636a5255990f734d34266b3b2e4a678b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="order-processing-with-policy"></a>İlke ile işlem sırası
Sipariş işleme ilkesi örnek sunulan anahtar özelliklerinden bazıları gösterir [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF). Aşağıdaki işlevleri WF kurallar altyapısı için yenidir:  
  
-   İşleç aşırı yüklemesi için destek.  
  
-   Desteği `new` işleci, kullanıcıların yeni nesneler ve diziler WF kurallardan oluşturmasına izin verme.  
  
-   Kullanıcı deneyimini WF kurallarından genişletme yöntemleri çağırma C stilleri # kodlama ile uyumlu hale getirmek genişletme yöntemleri için destek.  
  
> [!NOTE]
>  Bu örnek gerektiren [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] derlemek ve çalıştırmak için yüklenir. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Proje ve çözüm dosyalarını açmak için gereklidir.  
  
 Örnek gösteren bir `OrderProcessingPolicy` proje numaralandırılmış bir kullanılabilir öğeleri ve bir posta kodu listesinden oluşur, bir müşteri siparişi girilir. Her iki girişleri doğruysa sırasını başarıyla işlenir; Aksi takdirde hata nesneleri, bir aşırı yüklenmiş kullanılarak ilkesi oluşturur `+` işleci ve önceden tanımlanmış genişletme yöntemi hataları kullanıcıyı bilgilendirmek üzere.  
  
> [!NOTE]
>  Uzantı yöntemleri hakkında daha fazla bilgi için bkz: [C# sürüm 3.0 belirtimi](http://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Örnek aşağıdaki projeleri oluşmaktadır:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` Tanımlayan bir sınıf kitaplığı `OrderError` ve `OrderErrorCollection` sınıfları. Bir `OrderError` geçersiz bir giriş girildiğinde örneği oluşturulur. Kitaplık ayrıca bir genişletme yöntemi sağlar `OrderErrorCollection` çıkarır sınıfı `ErrorText` özelliği tüm `OrderError` nesnelerini `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` Projedir tek bir tanımlayan WF konsol uygulaması `PolicyFromFile` etkinlik. Etkinlik aşağıdaki kurallar vardır:  
  
    -   `invalidItemNum`  
  
         Bu kural öğesi numarası 1 ile 6, (bunlar dahil) arasında olduğunu doğrular. Madde numarası geçerli aralıkta ise, kural (dışında konsola yazdırma) hiçbir şey yapmaz. Madde numarası 1 ile 6 arasında değilse `invalidItemNum` kural aşağıdakileri yapar:  
  
        1.  Yeni bir `OrderError` nesne, maddeye geçirme girilen ve ayarlar `ErrorText` ve `CustomerName` nesne üzerindeki özellikleri.  
  
        2.  Oluşturur bir `invalidItemNumErrorCollection` nesne.  
  
        3.  Yeni oluşturulan ekler `OrderError` için örnek `invalidItemNumErrorCollection`.  
  
         Bu desteği gösterir `new` ile örneği nesneleri kuralları içine işleci.  
  
    -   `invalidZip`  
  
         Bu kural, posta kodu 5 rakamlı sahip ve için 600 99998 aralığı içinde doğrular. Posta kodu geçerli aralıkta ise, kural (dışında konsola yazdırma) hiçbir şey yapmaz. Posta kodu uzunluğu 5'ten az veya posta kodu 00600 ve 99998, arasında değil `invalidZip` kural aşağıdakileri yapar:  
  
        1.  Oluşturur bir `OrderError` nesnesi, girilen, posta kodu geçirme ve ayarlar `ErrorText` ve `CustomerName` nesne üzerindeki özellikleri.  
  
        2.  Oluşturur bir `invalidZipCodeErrorCollection` nesne.  
  
        3.  Yeni oluşturulan ekler `OrderError` yeni oluşturulan örneğine `invalidZipCodeErrorCollection`.  
  
         Bu kural için destek yeniden gösteren `new` nesneleri kuralları içine örneği olanak tanıyan işleci.  
  
    -   `displayErrors`  
  
         Bu kural, önceki iki kural iki tarafından eklenen herhangi bir hata olup olmadığını görmek için denetler `OrderErrorCollection` nesneleri `invalidItemNumErrorCollection` ve `invalidIZipCodeErrorCollection`. Hatalar varsa (ya da `invalidItemNumErrorCollection` veya `invalidZipCodeErrorCollection` değil `null`), kural aşağıdakileri yapar:  
  
        1.  Aşırı yüklenmiş çağırır `+` içeriğini kopyalamak için işleci `invalidItemNumErrorCollection` ve `invalidZipCodeErrorCollection` için bir `invalidOrdersCollection``OrderErrorCollection` örneği.  
  
        2.  Çağrıları `PrintOrderErrors` genişletme yöntemi `invalidOrdersCollection` ve çıkaran `ErrorText` özelliği tüm `orderError` nesnelerini `invalidOrdersCollection`.  
  
 Aşırı yüklenmiş işleci `+` üzerinde `OrderErrorCollection` tanımlanan `OrderErrorCollection` sınıfı, buna `OrderErrorLibrary` projesi. İki alan `OrderErrorCollection` nesneleri ve bunları tek istekte birleştirir `OrderErrorCollection` nesnesi.  
  
 `PrintOrderErrors` Genişletme yöntemi tanımlanan de `OrderErrorLibrary` projesi. Genişletme yöntemleri, buradan bir sınıf türetin veya özgün türü derlenir gerek kalmadan mevcut bir CLR türü ortak sözleşmesi için yeni yöntemler eklemek için geliştiricilere sağlayan bir yeni C# özelliğidir.  
  
 Örnek çalıştırdığınızda, bir ad, satın alınması için öğeyi öğe sayısını ve bir posta kodu girmeniz istenir. Bu bilgiler daha sonra ilke etkinliğinde tanımlanan kurallar tarafından doğrulanır. Program dosyasından örnek çıktı verilmiştir.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  OrderProcessingPolicy.sln proje dosyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümde iki farklı projelere vardır: `OrderErrorLibrary` ve `OrderProcessingPolicy`. `OrderProcessingPolicy` Proje kullanır sınıflar ve yöntemler tanımlanan `OrderErrorLibrary`.  
  
3.  Tüm projeleri oluşturun.  
  
4.  **Çalıştır**'ı tıklayın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`