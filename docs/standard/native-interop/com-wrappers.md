---
title: COM Sarmalayıcıları
description: COM istemcileri ve .NET nesneleri, COM çağrılabilir bir sarmalayıcı ve çalışma zamanında çağrılabilir sarmalayıcı kullanılarak etkileşim kurar. CLR sarmalayıcıları otomatik olarak oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: f1cf84b8f15de1e3bd19a391767f5573f01ff806
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420519"
---
# <a name="com-wrappers"></a>COM Sarmalayıcıları
COM, .NET çalışma zamanı nesne modelinden çeşitli önemli yollarla farklılık gösterir:  
  
- COM nesnelerinin istemcileri bu nesnelerin ömrünü yönetmelidir; ortak dil çalışma zamanı, ortamındaki nesnelerin ömrünü yönetir.  
  
- COM nesnelerinin istemcileri, bu hizmeti sağlayan bir arabirim isteyerek bir hizmetin kullanılabilir olup olmadığını ve bir arabirim işaretçisi geri almanızı bulur. .NET nesnelerinin istemcileri, yansıma kullanarak bir nesnenin işlevselliğinin açıklamasını elde edebilir.  
  
- NET nesneleri .NET çalışma zamanı yürütme ortamı tarafından yönetilen bellekte bulunur. Yürütme ortamı, performans nedenleriyle nesneleri belleğin etrafında taşıyabilir ve hareket yaptığı nesnelere tüm başvuruları güncelleştirebilir. Bir nesnenin işaretçisini elde eden yönetilmeyen istemciler, aynı konumda kalmak için nesnesine bağımlıdır. Bu istemciler, konumu düzeltilmeyen bir nesneyle ilgili bir mekanizmaya sahip değildir.  
  
 Bu farklılıkları aşmak için, çalışma zamanı, hem yönetilen hem de yönetilmeyen istemcilerin kendi ortamları içinde nesne aramasını düşündüğünü sağlamak için sarmalayıcı sınıflar sağlar. Yönetilen istemciniz bir COM nesnesinde bir yöntem çağırdığında, çalışma zamanı, bir [çalışma zamanı çağrılabilir sarmalayıcı](runtime-callable-wrapper.md) (RCW) oluşturur. RCWs, yönetilen ve yönetilmeyen başvuru mekanizmaları arasındaki farklılıkları diğer şeyler arasında soyutlar. Çalışma zamanı, işlemi tersine çevirmek için bir [com çağrılabilir sarmalayıcı](com-callable-wrapper.md) (CCW) oluşturur ve bir com istemcisinin bir .net nesnesine sorunsuz bir şekilde çağrı çağırmasını sağlar. Aşağıdaki çizimde gösterildiği gibi, çağıran kodun perspektifi, çalışma zamanının hangi sarmalayıcı sınıfını oluşturduğunu belirler.  
  
 ![COM sarmalayıcı genel bakış](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 Çoğu durumda, çalışma zamanı tarafından oluşturulan standart RCW veya CCW, COM ile .NET çalışma zamanı arasında sınır alan çağrılar için yeterli sıralama sağlar. Özel öznitelikleri kullanarak, isteğe bağlı olarak, çalışma zamanının yönetilen ve yönetilmeyen kodu temsil ettiği yöntemi ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 'de gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Çalışma Zamanı Aranabilir Sarmalayıcısı](runtime-callable-wrapper.md)
- [COM Aranabilir Sarmalayıcısı](com-callable-wrapper.md)
- [.NET Framework 'de standart sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Nasıl yapılır: .NET Framework içindeki çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))
