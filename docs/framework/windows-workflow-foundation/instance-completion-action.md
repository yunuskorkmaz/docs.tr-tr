---
title: Örnek Tamamlama Eylemi
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044338"
---
# <a name="instance-completion-action"></a>Örnek Tamamlama Eylemi

SQL Iş akışı örneği deposunun **örnek tamamlama eylemi** özelliği, iş akışı örneklerinin verilerin ve meta verilerinin, örnekler tamamlandıktan sonra kalıcılık veritabanından silinip silinmeyeceğini belirtmenize olanak tanır. Bu özellik için izin verilen değerler **DeleteAll** ve **deletenoin**' dir. Aşağıdaki listede bu seçenekler açıklanmaktadır:

- **DeleteAll (varsayılan).** Özelliğin değeri DeleteAll olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra kalıcılık veritabanından silinir.

- **Deletenoşeyi.** Özelliğin değeri Deletenoto olarak ayarlandıysa, iş akışı örneklerinin verileri ve meta verileri, örnekler tamamlandıktan sonra bile Kalıcılık veritabanında tutulur.

  > [!CAUTION]
  > Örneklerin tamamlanmasının ardından örnek durum bilgilerinin tutulması, kalıcılık veritabanının boyutunun büyümesine neden olur. Veritabanının boyutu, Kalıcılık alt sisteminin daha uzun sürdüğü veritabanı işlemlerini büyüdüğü için, hizmet durumlarını karşılayan bir düzeyde gerçekleştirmek için, kalıcılık veritabanından örnek durum bilgilerini düzenli aralıklarla temizlemeniz gerekir. performans ihtiyaçları.
