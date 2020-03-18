---
title: Güvenlik ve Kullanıcı Girdisi
description: Kodunuz, kullanıcı tarafından girilen verileri, güvenliği etkileyebilecek diğer kodlara parametre olarak geçirebilir. Sorunlu girişi reddetmek için aralık denetimi yapabilirsiniz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186101"
---
# <a name="security-and-user-input"></a>Güvenlik ve Kullanıcı Girdisi

Her türlü girdi (Web isteği veya URL'den alınan veriler, Microsoft Windows Forms uygulamasının denetimlerine giriş vb.) kullanıcı verileri, genellikle bu veriler diğer kodları aramak için doğrudan parametre olarak kullanıldığından kodu olumsuz etkileyebilir. Bu durum, kodunuzu garip parametrelerle çağıran kötü amaçlı koda benzer ve aynı önlemler alınmalıdır. Kullanıcı girişinin güvenli olması aslında zordur, çünkü güvenilmeyen verilerin varlığını izlemek için yığın çerçevesi yoktur.

Bunlar, güvenlikle ilgisi olmayan bir kodda bulunabilseler de, kötü verileri diğer kodlara aktarmak için bir ağ geçidi olduğundan, bulunması en ince ve en zor güvenlik hataları arasındadır. Bu hataları aramak için, her türlü giriş verilerini izleyin, olası değerlerin aralığının ne olabileceğini hayal edin ve bu verileri gören kodun tüm bu servis taleplerini işleyip işlemeyebileceğini düşünün. Bu hataları, kodun işleyemeyeceği herhangi bir girişi aralık denetimi ve reddederek düzeltebilirsiniz.

Kullanıcı verilerini içeren bazı önemli hususlar şunlardır:

- Sunucu yanıtındaki tüm kullanıcı verileri istemcide sunucunun sitesi bağlamında çalışır. Web sunucunuz kullanıcı verilerini alıp döndürülen Web sayfasına eklerse, örneğin ** \<** bir komut dosyası>etiketi ekleyebilir ve sunucudan geliyormuş gibi çalıştırAbilir.

- İstemcinin herhangi bir URL isteyebileceğini unutmayın.

- Zor veya geçersiz yolları göz önünde bulundurun:

  - .. \ , son derece uzun yollar.

  - Joker karakter kullanımı (*).

  - Belirteç genişlemesi (%token%).

  - Özel anlamı olan yolların garip formları.

  - Alternatif dosya sistemi akışı `filename::$DATA`adları gibi .

  - için `longfi~1` `longfilename`gibi dosya adlarının kısa sürümleri.

- Eval'in (userdata) her şeyi yapabileceğini unutmayın.

- Bazı kullanıcı verilerini içeren bir ada geç bağlanmakonusunda dikkatli olun.

- Web verileriyle ilgileniyorsanız, aşağıdakiler de dahil olmak üzere izin verilen çeşitli kaçış biçimlerini göz önünde bulundurun:

  - Hexadecimal kaçışlar (%nn).

  - Unicode kaçar (%nnn).

  - Overlong UTF-8 kaçar (%nn%nn).

  - Çift kaçış (%nn %mmnn olur, %mm '%') için kaçış olur.

- Birden fazla kanonik biçimi olabilecek kullanıcı adlarıyla dikkatli olun. Örneğin,\\mydomain*kullanıcı adı* formunu veya kullanıcı *adı* @mydomain.example.com formunu sık sık kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
