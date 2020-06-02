---
title: Güvenlik ve Kullanıcı Girdisi
description: Kodunuz, Kullanıcı tarafından girilen verileri diğer koda parametre olarak geçirebilir ve bu da güvenliği etkileyebilir. Sorunlu girişi reddetmek için Aralık denetimi yapabilirsiniz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 995af30385790a88718193e7abad1db7bc4b56c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84275951"
---
# <a name="security-and-user-input"></a>Güvenlik ve Kullanıcı Girdisi

Her türlü giriş (bir Web isteği veya URL 'deki veriler, bir Microsoft Windows Forms uygulamasının denetimlerine giriş vb.) olan Kullanıcı verileri, genellikle bu veriler diğer kodu çağırmak için parametre olarak doğrudan kullanıldığı için kodu olumsuz etkileyebilir. Bu durum, kodunuzu garip parametrelerle çağıran kötü amaçlı koda benzer ve aynı önlemler alınmalıdır. Potansiyel olarak güvenilmeyen verilerin varlığını izlemek için yığın çerçevesi bulunmadığından, Kullanıcı girişi gerçekten güvenli hale getirmek daha zordur.

Bunlar, güvenlikle ilgili olmayan bir kodda bulunabilseler de, güvenlikle ilgili olan ve diğer koda yönelik hatalı verileri geçirmeye yönelik bir ağ geçidinizin olan alt en uzun ve en yüksek güvenlik hatalarının arasındadır. Bu hataları aramak için, her türlü giriş verilerini izleyin, olası değerlerin aralığının ne olabileceğini düşünün ve bu verileri gördüğü kodun tüm bu durumları işleyebileceğini göz önünde bulundurun. Bu hataları Aralık denetleme ve kodun işleyemeyeceği herhangi bir girişi reddetme yoluyla çözebilirsiniz.

Kullanıcı verileriyle ilgili bazı önemli noktalar şunlardır:

- Sunucu yanıtındaki herhangi bir kullanıcı verisi, istemci üzerindeki sunucunun sitesi bağlamında çalışır. Web sunucunuz kullanıcı verilerini alıp döndürülen Web sayfasına eklediğinde, örneğin bir **\<script>** etiketi içerebilir ve sunucuda olduğu gibi çalıştırabilirsiniz.

- İstemcinin herhangi bir URL isteyeolabileceğini unutmayın.

- Karmaşık veya geçersiz yolları göz önünde bulundurun:

  - .. \, son derece uzun yollar.

  - Joker karakter (*) kullanın.

  - Belirteç genişletmesi (% token%).

  - Özel anlamlara sahip garip yol biçimleri.

  - Gibi alternatif dosya sistemi akış adları `filename::$DATA` .

  - İçin gibi dosya adlarının kısa sürümleri `longfi~1` `longfilename` .

- Eval (UserData) her şeyi yapabildiği unutulmamalıdır.

- Bazı Kullanıcı verilerini içeren bir ada geç bağlama konusunda dikkatli olun.

- Web verileriyle uğraşıyorsanız, aşağıdakiler de dahil olmak üzere, izin verilen çeşitli kaçış biçimlerini göz önünde bulundurun:

  - Onaltılı kaçış (% nn).

  - Unicode kaçış (% nnn).

  - Fazla uzun UTF-8 kaçış (% nn% nn).

  - Çift kaçış (% nn,% mm '% ' için kaçış olduğu için% mmnn olur).

- Birden fazla kurallı biçimi olabilecek kullanıcı adlarına karşı dikkatli olun. Örneğin, genellikle ETKIALANıM \\ *Kullanıcı adı* formunu veya *Kullanıcı adı* @mydomain.example.com formunu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](secure-coding-guidelines.md)
