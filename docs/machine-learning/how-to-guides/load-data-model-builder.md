---
title: Model Oluşturucu için yükleme eğitim verileri
description: ML.NET için Model Oluşturucu senaryolarından birinde kullanılmak üzere bir SQL Server veritabanından veya bir dosyadan eğitim verilerini nasıl yükleyin öğrenin.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849165"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="f9ac6-103">Eğitim verilerini Model Oluşturucu'ya yükleyin</span><span class="sxs-lookup"><span data-stu-id="f9ac6-103">Load training data into Model Builder</span></span>

<span data-ttu-id="f9ac6-104">ML.NET için Model Oluşturucu senaryolarından birinde kullanılmak üzere bir dosyadan veya SQL Server veritabanından eğitim veri kümelerinizi nasıl yükleyebilirsiniz öğrenin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="f9ac6-105">Model Oluşturucu senaryoları, SQL Server veritabanlarını, görüntü dosyalarını ve CSV veya TSV dosya biçimlerini eğitim verileri olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="f9ac6-106">Model Oluşturucu'da veri kümesi sınırlamalarını geliştirme</span><span class="sxs-lookup"><span data-stu-id="f9ac6-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="f9ac6-107">Model Oluşturucu, eğitim modelleri için kullanabileceğiniz veri miktarını ve türünü sınırlar:</span><span class="sxs-lookup"><span data-stu-id="f9ac6-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="f9ac6-108">SQL Server verileri: 100.000 satır</span><span class="sxs-lookup"><span data-stu-id="f9ac6-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="f9ac6-109">CSV ve TSV dosyaları: Boyut sınırı yok</span><span class="sxs-lookup"><span data-stu-id="f9ac6-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="f9ac6-110">Görüntüler: Sadece PNG ve JPG.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="f9ac6-111">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="f9ac6-111">Model Builder scenarios</span></span>

<span data-ttu-id="f9ac6-112">Model Oluşturucu, aşağıdaki makine öğrenimi senaryoları için modeller oluşturmanıza yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="f9ac6-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="f9ac6-113">Duyarlılık analizi (ikili sınıflandırma): Metinsel verileri iki kategoriye ayırın.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="f9ac6-114">Sorun sınıflandırması (çok sınıflı sınıflandırma): Metin verilerini 3 veya daha fazla kategoriye ayırın.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="f9ac6-115">Fiyat tahmini (regresyon): Sayısal bir değeri tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="f9ac6-116">Görüntü sınıflandırması (derin öğrenme): Görüntüleri özelliklerine göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="f9ac6-117">Özel senaryo: Regresyon, sınıflandırma ve diğer görevleri kullanarak verilerinizden özel senaryolar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="f9ac6-118">Bu makalede, metinsel veya sayısal verilerle sınıflandırma ve regresyon senaryoları ve görüntü sınıflandırma senaryoları ele alınız.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="f9ac6-119">Dosyadan metin veya sayısal veri yükleme</span><span class="sxs-lookup"><span data-stu-id="f9ac6-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="f9ac6-120">Bir dosyadaki metin veya sayısal verileri Model Oluşturucu'ya yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="f9ac6-121">Virgülle sınırlandırılmış (CSV) veya sekme-sınırlandırma (TSV) dosya biçimlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="f9ac6-122">Model Oluşturucu'nun veri adımında, veri kaynağı açılır tarafından **Dosya'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="f9ac6-123">Dosya metin kutusunu **seç'in** yanındaki düğmeyi seçin ve veri dosyasına göz atmak ve seçmek için Dosya Gezgini'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="f9ac6-124">**Sütunda Tahmin (Etiket)** açılır düşüşünü tahmin etmek için bir kategori seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="f9ac6-125">Giriş **Sütunları (Özellikler)** açılır düşüşünden, eklemek istediğiniz veri sütunlarının denetleniyi onaylayın.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="f9ac6-126">Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı bitirdiniz.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="f9ac6-127">Model Oluşturucu'da bir sonraki adıma geçmek için **Tren** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="f9ac6-128">SQL Server veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="f9ac6-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="f9ac6-129">Model Oluşturucu, yerel ve uzak SQL Server veritabanlarından veri yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="f9ac6-130">SQL Server veritabanından Modül Oluşturucu'ya veri yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="f9ac6-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="f9ac6-131">Model Oluşturucu'nun veri adımında, veri kaynağı açılır tarafından **SQL Server'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="f9ac6-132">**SQL Server veritabanına bağlan** metin kutusunun yanındaki düğmeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="f9ac6-133">Veri **Seç** iletişim kutusunda **Microsoft SQL Server Database File'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="f9ac6-134">**Her Zaman bu seçim** onay kutusunu kullan denetiminden kaldırın ve Devam **et'i** seçin</span><span class="sxs-lookup"><span data-stu-id="f9ac6-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="f9ac6-135">Bağlantı **Özellikleri** iletişim kutusunda **Gözat'ı** seçin ve indirilenleri seçin. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="f9ac6-136">**Tamam'ı** seçin</span><span class="sxs-lookup"><span data-stu-id="f9ac6-136">Select **OK**</span></span>
1. <span data-ttu-id="f9ac6-137">**Tablo Adı** açılır toplantısından veri kümesi adını seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="f9ac6-138">**Sütundan Tahmin (Etiket)** açılır goluna kadar, tahmin de bulunmak istediğiniz veri kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="f9ac6-139">Giriş **Sütunları (Özellikler)** açılır düşüşünden, eklemek istediğiniz sütunların kontrol edildiğini onaylayın.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="f9ac6-140">Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı bitirdiniz.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="f9ac6-141">Model Oluşturucu'da bir sonraki adıma geçmek için **Tren** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="f9ac6-142">Görüntü veri dosyalarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="f9ac6-142">Set up image data files</span></span>

<span data-ttu-id="f9ac6-143">Model Builder, görüntü verilerinin sınıflandırma kategorilerine karşılık gelen klasörlerde düzenlenmiş JPG veya PNG dosyaları olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="f9ac6-144">Görüntüleri Model Oluşturucu'ya yüklemek için, tek bir üst düzey dizin için yol sağlayın:</span><span class="sxs-lookup"><span data-stu-id="f9ac6-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="f9ac6-145">Bu üst düzey dizin, her kategoriiçin tahmin etmek için bir alt klasör içerir.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="f9ac6-146">Her alt klasör kendi kategorisine ait resim dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="f9ac6-147">Aşağıda gösterilen klasör yapısında, üst düzey dizin *flower_photos.*</span><span class="sxs-lookup"><span data-stu-id="f9ac6-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="f9ac6-148">Tahmin etmek istediğiniz kategorilere karşılık gelen beş alt dizin vardır: papatya, karahindiba, gül, ayçiçeği ve lale.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="f9ac6-149">Bu alt dizinlerin her biri kendi kategorisine ait görüntüler içerir.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a><span data-ttu-id="f9ac6-150">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f9ac6-150">Next steps</span></span>

<span data-ttu-id="f9ac6-151">Model Builder ile makine öğrenimi uygulamaları oluşturmak için aşağıdaki öğreticileri izleyin:</span><span class="sxs-lookup"><span data-stu-id="f9ac6-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="f9ac6-152">Gerileme kullanarak fiyatları tahmin edin</span><span class="sxs-lookup"><span data-stu-id="f9ac6-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="f9ac6-153">İkili sınıflandırmayı kullanarak bir web uygulamasında ki duyarlılığı analiz edin</span><span class="sxs-lookup"><span data-stu-id="f9ac6-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="f9ac6-154">Kodu kullanarak bir modeli eğittiyseniz, [ML.NET API'yi kullanarak verileri nasıl yükleyeceğimiz öğrenin.](load-data-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="f9ac6-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
