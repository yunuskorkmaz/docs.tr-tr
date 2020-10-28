---
title: Derleme konumu
description: .NET derlemesinin konumu, CLR 'nin onu nasıl bulduğunu ve diğer Derlemelerle paylaşılıp paylaşılamayacağını belirler.
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 1fa1c486c0cddce4ddcfae7f2df27e2e85c88e66
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687599"
---
# <a name="assembly-location"></a>Derleme konumu

Bir derlemenin konumu, ortak dil çalışma zamanının başvurulması sırasında bulup belirleyemeyeceğini belirler ve derlemenin diğer Derlemelerle paylaşılıp paylaşılamayacağını da tespit edebilir. Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:

- Uygulamanın dizini veya alt dizinleri.

     Bu, bir derlemeyi dağıtmaya yönelik en yaygın konumdur. Bir uygulamanın kök dizininin alt dizinleri dil veya kültür temelinde olabilir. Bir derlemenin kültür özniteliğinde bilgileri varsa, bu kültür adına sahip uygulama dizini altındaki bir alt dizinde olmalıdır.

- Genel derleme önbelleği.

     Bu, ortak dil çalışma zamanının yüklendiği her yerde yüklenen makine genelindeki bir kod önbelleğidir. Çoğu durumda, birden çok uygulamayla bir derlemeyi paylaşmayı düşünüyorsanız, onu genel derleme önbelleğine dağıtmanız gerekir.

- Bir HTTP sunucusunda.

     HTTP sunucusunda dağıtılan bir derlemenin tanımlayıcı adı olması gerekir; uygulamanın yapılandırma dosyasının kod temeli bölümünde derleme üzerine gelin.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme oluşturma](create.md)
- [Genel derleme önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
