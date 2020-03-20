---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857262"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen=False ile Zincirli Açılır Pencereler

|   |   |
|---|---|
|Ayrıntılar|StaysOpen=False olan bir Pop-up'ın Pop-up'ın dışında tıkladığınızda kapanması gerekir. İki veya daha fazla pop-up zincirli olduğunda (yani biri diğerini içerir), aşağıdakiler de dahil olmak üzere birçok sorun vardı:<ul><li>İki düzeyleri açın, P2 dışında ama P1 içinde tıklatın.  Hiçbir şey olmuyor.</li><li>İki seviye açın, P1'in dışına tıklayın.  Her iki pop-up yakın.</li><li>İki seviyeyi açın ve kapatın.  Sonra tekrar P2 açmayı deneyin.  Hiçbir şey olmuyor.</li><li>Üç seviyeleri açmaya çalışın.  Bunu yapamazsınız.  (Tıklattığınız yere bağlı olarak, hiçbir şey olmaz veya ilk iki seviye kapanır.) Bu servis talepleri (ve diğer türevleri) artık beklendiği gibi çalışır.</li></ul>|
|Kapsam|Edge|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
