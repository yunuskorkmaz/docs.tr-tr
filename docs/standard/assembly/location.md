---
title: Derleme konumu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733133"
---
# <a name="assembly-location"></a>Derleme konumu
Bir derlemenin konumu, ortak dil çalışma zamanının başvurulduğunda onu bulup bulamayacağını belirler ve derlemenin diğer derlemelerle paylaşılıp paylaşılamayacağını da belirler. Bir derlemeyi aşağıdaki konumlara dağıtabilirsiniz:

- Uygulamanın dizin veya alt dizinleri.

     Bu, bir derlemedağıtmak için en yaygın konumdur. Bir uygulamanın kök dizininin alt dizinleri dil veya kültüre dayalı olabilir. Bir derlemekültür özniteliği bilgi varsa, bu kültürün adı ile uygulama dizininin altında bir alt dizini olmalıdır.

- Genel derleme önbelleği.

     Bu, ortak dil çalışma zamanının yüklendiğinde, makine çapında bir kod önbelleğidir. Çoğu durumda, bir derlemeyi birden çok uygulamayla paylaşmayı planlıyorsanız, derlemeyi genel derleme önbelleğine dağıtmanız gerekir.

- Bir HTTP sunucusunda.

     BIR HTTP sunucusunda dağıtılan bir derlemenin güçlü bir adı olmalıdır; uygulamanın yapılandırma dosyasının codebase bölümünde derlemeişaret.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme oluşturma](create.md)
- [Genel montaj önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanı derlemeleri nasıl bulur?](../../framework/deployment/how-the-runtime-locates-assemblies.md)
