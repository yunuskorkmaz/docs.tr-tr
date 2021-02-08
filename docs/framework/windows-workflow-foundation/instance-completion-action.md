---
description: 'Daha fazla bilgi edinin: örnek tamamlama eylemi'
title: Örnek Tamamlama Eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 84405ca9869369e4fe00b0049d628671a79a9f68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792693"
---
# <a name="instance-completion-action"></a>Örnek Tamamlama Eylemi

SQL Iş akışı örneği deposunun **örnek tamamlama eylemi** özelliği, iş akışı örneklerinin verilerin ve meta verilerinin, örnekler tamamlandıktan sonra kalıcılık veritabanından silinip silinmeyeceğini belirtmenize olanak tanır. Bu özellik için izin verilen değerler **DeleteAll** ve **deletenoin**' dir. Aşağıdaki listede bu seçenekler açıklanmaktadır:

- **DeleteAll (varsayılan).** Özelliğin değeri DeleteAll olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra kalıcılık veritabanından silinir.

- **Deletenoşeyi.** Özelliğin değeri Deletenoto olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra bile Kalıcılık veritabanında tutulur.

  > [!CAUTION]
  > Örneklerin tamamlanmasının ardından örnek durum bilgilerinin tutulması, kalıcılık veritabanının boyutunun büyümesine neden olur. Veritabanının boyutu, Kalıcılık alt sisteminin daha uzun sürdüğü veritabanı işlemlerini büyüdüğü için, performans ihtiyaçlarınızı karşılayan düzeyde Hizmetleri gerçekleştirmek üzere Kalıcılık veritabanından örnek durum bilgilerini düzenli aralıklarla temizlemeniz gerekir.
