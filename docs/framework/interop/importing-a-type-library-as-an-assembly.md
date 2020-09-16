---
title: Tür Kitaplığını Derleme Olarak İçeri Aktarma
description: Bir derleme olarak COM tür tanımlarını içeren bir tür kitaplığı içeri aktarın. Bir tür kitaplığından meta veri oluşturmanın yollarını öğrenin ve bu bir birlikte çalışma derlemesine yol açar.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
ms.openlocfilehash: bc1b921fea5aff086e21c046369f1d461f553bc7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554690"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Tür Kitaplığını Derleme Olarak İçeri Aktarma

COM tür tanımları genellikle bir tür kitaplığında bulunur. Buna karşılık, CLS uyumlu derleyiciler bir derlemede tür meta verileri üretir. Tür bilgilerinin iki kaynağı oldukça farklıdır. Bu konu, bir tür kitaplığından meta veri oluşturma tekniklerini açıklamaktadır. Elde edilen derlemeye birlikte çalışma derlemesi denir ve içerdiği tür bilgileri .NET Framework uygulamaların COM türlerini kullanmasını sağlar.

Bu tür bilgilerini uygulamanız için kullanılabilir hale getirmek için iki yol vardır:

- Yalnızca tasarım zamanı birlikte çalışma derlemelerini kullanarak: .NET Framework 4 ' ten başlayarak, derleyicinin birlikte çalışma derlemesinden tür bilgilerini çalıştırılabilire katıştırmasını isteyebilirsiniz. Derleyici yalnızca uygulamanızın kullandığı tür bilgilerini katıştırır. Birlikte çalışma derlemesini uygulamanızla birlikte dağıtmanız gerekmez. Önerilen yöntem budur.

- Birlikte çalışma derlemelerini dağıtma: birlikte çalışma derlemesine standart bir başvuru oluşturabilirsiniz. Bu durumda, birlikte çalışma derlemesinin uygulamanızla birlikte dağıtılması gerekir. Bu tekniği kullandıysanız ve özel bir COM bileşeni kullanmıyorsanız, her zaman yönetilen kodunuzda birleştirmek istediğiniz COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesine (PIA) başvurun. Birincil birlikte çalışma derlemelerini üretme ve kullanma hakkında daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

Yalnızca tasarım zamanı birlikte çalışma derlemelerini kullandığınızda, COM bileşeninin yazarı tarafından yayımlanan birincil birlikte çalışma derlemesinden tür bilgilerini ekleyebilirsiniz. Bununla birlikte, birincil birlikte çalışma derlemesini uygulamanızla birlikte dağıtmanız gerekmez.

Çoğu uygulama bir COM bileşeninin tüm özelliklerini kullanmadığından, yalnızca tasarım zamanı birlikte çalışma derlemelerini kullanmak uygulamanızın boyutunu azaltır. Derleyici tür bilgilerini katıştıran çok verimlidir; uygulamanız bir COM arabiriminde yöntemlerin yalnızca bazılarını kullanıyorsa, derleyici kullanılmayan yöntemleri eklemez. Gömülü tür bilgilerine sahip bir uygulama, başka bir uygulamayla etkileşime geçtiğinde veya birincil birlikte çalışma derlemesini kullanan bir uygulamayla etkileşime geçtiğinde, ortak dil çalışma zamanı, aynı ada sahip iki türün aynı COM türünü temsil ettiğini anlamak için tür denklik kurallarını kullanır. COM nesnelerini kullanmak için bu kuralları bilmeniz gerekmez. Ancak kurallarla ilgileniyorsanız, bkz. [tür denklik ve katıştırılmış birlikte çalışma türleri](type-equivalence-and-embedded-interop-types.md).

## <a name="generating-metadata"></a>Meta veriler üretiliyor

COM tür kitaplıkları, Krelib. tlb gibi. tlb uzantılı tek başına dosyalar olabilir. Bazı tür kitaplıkları bir. dll veya. exe dosyasının kaynak bölümüne katıştırılır. Kitaplık bilgisi türündeki diğer kaynaklar. olb ve. ocx dosyalarıdır.

Hedef COM türü uygulamasını içeren tür kitaplığını bulduktan sonra, tür meta verilerini içeren bir birlikte çalışma derlemesi oluşturmak için aşağıdaki seçeneklere sahip olursunuz:

- Visual Studio

  Visual Studio, bir tür kitaplığındaki COM türlerini otomatik olarak bir derlemedeki meta verilere dönüştürür. Yönergeler için bkz. [nasıl yapılır: tür kitaplıklarına başvurular ekleme](how-to-add-references-to-type-libraries.md).

- [Tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)

  Tür kitaplığı alma programı, elde edilen birlikte çalışma dosyasındaki meta verileri ayarlamak için komut satırı seçenekleri sağlar, türleri varolan bir tür kitaplığından içeri aktarır ve bir birlikte çalışma derlemesi ve bir ad alanı oluşturur. Yönergeler için bkz. [nasıl yapılır: tür kitaplıklarından birlikte çalışma derlemeleri oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md).

- <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> sınıfı

  Bu sınıf, bir tür kitaplığındaki ortak sınıfları ve arabirimleri derleme içindeki meta verilere dönüştürmek için yöntemler sağlar. Tlbimp.exe aynı meta veri çıkışını üretir. Ancak, Tlbimp.exe aksine sınıfı, <xref:System.Runtime.InteropServices.TypeLibConverter> bellek içi bir tür kitaplığını meta verilere dönüştürebilir.

- Özel sarmalayıcılar

  Bir tür kitaplığı kullanılamadığında veya yanlış olduğunda, yönetilen kaynak kodunda sınıfın veya arabirimin yinelenen tanımını oluşturmak için bir seçenek vardır. Ardından, bir derlemede meta veri üretmek için çalışma zamanını hedefleyen bir derleyici ile kaynak kodu derleyebilirsiniz.

  COM türlerini el ile tanımlamak için aşağıdaki öğelere erişiminizin olması gerekir:

  - Tanımlanmakta olan coclass 'ları ve arabirimlerin kesin açıklamaları.

  - C# derleyicisi gibi uygun .NET Framework sınıf tanımlarını oluşturabilen bir derleyici.

  - Kitaplık-derleme dönüştürme kuralları türü hakkında bilgi.

  Özel sarmalayıcı yazmak gelişmiş bir tekniktir. Özel bir sarmalayıcı oluşturma hakkında daha fazla bilgi için bkz. [Standart sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).

 COM birlikte çalışabilirlik içeri aktarma işlemi hakkında daha fazla bilgi için bkz. [tür kitaplığına derleme dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
- [Tür kitaplığını derlemeye dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md)
- [Standart sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Yönetilen kodda COM türlerini kullanma](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Birlikte Çalışma Projesi Derleme](compiling-an-interop-project.md)
- [Birlikte Çalışma Uygulamasını Dağıtma](deploying-an-interop-application.md)
- [Nasıl yapılır: Tür Kitaplıklarına Başvurular Ekleme](how-to-add-references-to-type-libraries.md)
- [Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma](how-to-generate-interop-assemblies-from-type-libraries.md)
