---
title: Güvenlik ve Kullanıcı Girdisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce6dd2fcf913c16e4da68dec35ea3ccd8e90a948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665778"
---
# <a name="security-and-user-input"></a>Güvenlik ve Kullanıcı Girdisi
Herhangi türde bir girdi (veriler bir Web isteği veya URL, bir Microsoft Windows Forms uygulaması ve benzeri denetimleri için giriş), bu verileri diğer kod çağırmak için doğrudan parametre olarak sıklıkla kullanılır çünkü kod olumsuz yönde etkileyebilir kullanıcı verileri. Bu durum kötü amaçlı kod kodunuzu garip parametrelerle çağırılıyor benzerdir ve aynı önlemler dikkat edilmelidir. Kullanıcı Giriş potansiyel olarak güvenilmeyen veri izlemek için hiçbir yığın çerçevesi olduğundan güvenli hale getirmek için gerçekten daha zor olabilir.  
  
 Bu, başka bir kod aracılığıyla hatalı veri iletmek için bir ağ geçidi olduğundan, güvenlik görünüşte ilgisiz olan kod bulunabilir ancak bunlar bulmak için belirsiz ve uygulamalarınızdaki güvenlik hatalar arasındadır. Bu hatalar için aramak için giriş verileri herhangi bir türden izleyin, hangi olası değerleri aralığı olması ve bu verileri görme hakkındaki kod tüm durumlarda işlenip işlenmeyeceğini göz önünde bulundurun Imagine. Bu hatalar denetleme ve kodu işleyemiyor herhangi bir giriş reddetme aralığı düzeltebilirsiniz.  
  
 Kullanıcı verilerini içeren bazı önemli noktalar şunlardır:  
  
- Tüm kullanıcı verilerini bir sunucu yanıtı sunucunun site bağlamında istemcide çalıştırır. Web sunucunuzun kullanıcı verileri alır ve döndürülen Web sayfasına ekler, örneğin, içerebilir bir  **\<betik >** etiketleyin ve sunucudan gibi çalıştırın.  
  
- İstemcinin herhangi bir URL isteyebilir unutmayın.  
  
- Zor ya da geçersiz yolları göz önünde bulundurun:  
  
    - .. \, son derece uzun yollar.  
  
    - Joker karakter (*) kullanın.  
  
    - Belirteç genişletme (% belirteci %).  
  
    - Garip formları yolların özel anlama sahip.  
  
    - Dosya sistemi akışı adları gibi alternatif `filename::$DATA`.  
  
    - Dosya adlarının sürümleri gibi kısa `longfi~1` için `longfilename`.  
  
- Her şeyi yapabilirsiniz Eval(UserData) unutmayın.  
  
- Bazı kullanıcı verilerini içeren bir ad, geç bağlama dikkatli olun.  
  
- Web veri ile uğraşıyorsanız, çeşitli türleri dahil olmak üzere izin çıkar, göz önünde bulundurun:  
  
    - Onaltılık kaçış karakterleri (% nn).  
  
    - Unicode kaçış karakterleri (% nnn).  
  
    - Overlong UTF-8 çıkar (% nn % nn).  
  
    - Çift kaçış karakterleri (% nn % mm '%' kaçış olduğu, % mmnn olur).  
  
- Birden fazla kurallı biçimde olabilecek kullanıcı adlarını dikkatli olun. Örneğin, genellikle ya da MYDOMAIN kullanabilirsiniz\\*kullanıcıadı* form veya *kullanıcıadı* @mydomain.example.com form.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
