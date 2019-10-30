---
title: Model Oluşturucu için eğitim verilerini yükleme
description: ML.NET için model Oluşturucu senaryolarından birinde kullanılmak üzere bir SQL Server veritabanından veya bir dosyadan eğitim verileri yüklemeyi öğrenin.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 47dd32d18d00c33bcf51aa0ea3be8b22494ebc5f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041277"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="a7421-103">Eğitim verilerini model Oluşturucu 'ya yükleme</span><span class="sxs-lookup"><span data-stu-id="a7421-103">Load training data into Model Builder</span></span>

<span data-ttu-id="a7421-104">Eğitim veri kümelerinizi bir dosya veya SQL Server veritabanından, ML.NET için model Oluşturucu senaryolarından birinde kullanmak üzere nasıl yükleyeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="a7421-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="a7421-105">Model Oluşturucu senaryoları, eğitim verileri olarak SQL Server veritabanlarını, görüntü dosyalarını ve CSV 'yi ya da TSV dosya biçimlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a7421-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="a7421-106">Model Oluşturucu 'da eğitim veri kümesi sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="a7421-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="a7421-107">Model Oluşturucu, eğitim modelleri için kullanabileceğiniz veri miktarını ve türünü sınırlar:</span><span class="sxs-lookup"><span data-stu-id="a7421-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="a7421-108">SQL Server verileri: 100.000 satır</span><span class="sxs-lookup"><span data-stu-id="a7421-108">SQL Server data: 100,000 rows</span></span> 
- <span data-ttu-id="a7421-109">CSV ve TSV dosyaları: boyut sınırı yok</span><span class="sxs-lookup"><span data-stu-id="a7421-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="a7421-110">Görüntüler: yalnızca PNG ve JPG.</span><span class="sxs-lookup"><span data-stu-id="a7421-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="a7421-111">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="a7421-111">Model Builder scenarios</span></span> 

<span data-ttu-id="a7421-112">Model Oluşturucu aşağıdaki makine öğrenimi senaryoları için modeller oluşturmanıza yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="a7421-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="a7421-113">Yaklaşım Analizi (ikili sınıflandırma): metinsel verileri iki kategoride sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="a7421-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="a7421-114">Sorun sınıflandırması (birden çok Lass sınıflandırması): metinsel verileri 3 veya daha fazla kategoride sınıflandırın.</span><span class="sxs-lookup"><span data-stu-id="a7421-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="a7421-115">Fiyat tahmini (gerileme): sayısal bir değer tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="a7421-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="a7421-116">Görüntü sınıflandırması (derin öğrenme): görüntüleri özelliklere göre kategorilere ayırın.</span><span class="sxs-lookup"><span data-stu-id="a7421-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="a7421-117">Özel senaryo: gerileme, sınıflandırma ve diğer görevleri kullanarak verilerinize özel senaryolar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7421-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="a7421-118">Bu makale, metin veya sayısal verilerle sınıflandırma ve regresyon senaryolarına ve görüntü sınıflandırma senaryolarıyla birlikte ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7421-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span> 

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="a7421-119">Dosyadan metin veya sayısal veri yükleme</span><span class="sxs-lookup"><span data-stu-id="a7421-119">Load text or numeric data from a file</span></span>  

<span data-ttu-id="a7421-120">Bir dosyadaki metin veya sayısal verileri model Oluşturucu 'ya yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7421-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="a7421-121">Virgülle ayrılmış (CSV) veya sekmeyle ayrılmış (TSV) dosya biçimlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a7421-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span> 

1. <span data-ttu-id="a7421-122">Model oluşturucunun veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="a7421-123">**Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve veri dosyasına gidip seçmek Için dosya Gezgini 'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7421-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="a7421-124">**Tahmin edilecek sütun (etiket)** açılan listesinden bir kategori seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="a7421-125">**Giriş sütunları (Özellikler)** açılır listesinden, dahil etmek istediğiniz veri sütunlarının denetlenmesini onaylayın.</span><span class="sxs-lookup"><span data-stu-id="a7421-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="a7421-126">Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="a7421-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="a7421-127">Model Oluşturucu 'daki sonraki adıma geçmek için **eğitme** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="a7421-128">SQL Server veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="a7421-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="a7421-129">Model Oluşturucu, yerel ve uzak SQL Server veritabanlarından veri yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="a7421-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="a7421-130">SQL Server veritabanından modül Oluşturucusu 'na veri yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="a7421-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="a7421-131">Model oluşturucunun veri adımında, veri kaynağı açılır listesinden **SQL Server** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="a7421-132">**SQL Server veritabanına Bağlan** metin kutusunun yanındaki düğmeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="a7421-133">**Veri Seç** iletişim kutusunda **Microsoft SQL Server veritabanı dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span> 
    1. <span data-ttu-id="a7421-134">**Her zaman bu seçimi kullan** onay kutusunu temizleyin ve **devam** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="a7421-135">**Bağlantı özellikleri** iletişim kutusunda, **Araştır** ' ı seçin ve indirilen ' u seçin. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="a7421-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="a7421-136">**Tamam 'ı** seçin</span><span class="sxs-lookup"><span data-stu-id="a7421-136">Select **OK**</span></span>
1. <span data-ttu-id="a7421-137">**Tablo adı** açılan listesinden veri kümesi adını seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="a7421-138">**Sütunun tahmin edilmesi için (etiket)** aşağı açılan listesinden tahmin yapmak istediğiniz veri kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="a7421-139">**Giriş sütunları (Özellikler)** açılır listesinden, dahil etmek istediğiniz sütunları onaylayın.</span><span class="sxs-lookup"><span data-stu-id="a7421-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span> 

<span data-ttu-id="a7421-140">Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="a7421-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="a7421-141">Model Oluşturucu 'daki sonraki adıma geçmek için **eğitme** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="a7421-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="a7421-142">Görüntü veri dosyalarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="a7421-142">Set up image data files</span></span>

<span data-ttu-id="a7421-143">Model Oluşturucu, sınıflandırma kategorilerine karşılık gelen klasörlerde görüntü verilerinin JPG veya PNG dosyaları olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="a7421-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span> 

<span data-ttu-id="a7421-144">Model Oluşturucusu 'na görüntü yüklemek için, tek bir üst düzey dizinin yolunu belirtin:</span><span class="sxs-lookup"><span data-stu-id="a7421-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="a7421-145">Bu üst düzey dizin, tahmin edilecek kategorilerin her biri için bir alt klasör içerir.</span><span class="sxs-lookup"><span data-stu-id="a7421-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span> 
- <span data-ttu-id="a7421-146">Her alt klasör, kategorisine ait olan resim dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a7421-146">Each subfolder contains the image files belonging to its category.</span></span> 
 
<span data-ttu-id="a7421-147">Aşağıda gösterilen klasör yapısında, en üst düzey dizin *flower_photos*' dir.</span><span class="sxs-lookup"><span data-stu-id="a7421-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="a7421-148">Tahmin etmek istediğiniz kategorilere karşılık gelen beş alt dizin vardır: daya, Dandelion, Roses, sunçiçekler ve TULIP.</span><span class="sxs-lookup"><span data-stu-id="a7421-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="a7421-149">Bu alt dizinlerin her biri ilgili kategorisine ait resimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a7421-149">Each of these subdirectories contains images belonging to its respective category.</span></span> 

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

## <a name="next-steps"></a><span data-ttu-id="a7421-150">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a7421-150">Next steps</span></span>
<span data-ttu-id="a7421-151">Model Oluşturucu ile makine öğrenimi uygulamaları oluşturmak için bu öğreticileri izleyin:</span><span class="sxs-lookup"><span data-stu-id="a7421-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="a7421-152">Gerileme kullanarak fiyatları tahmin etme</span><span class="sxs-lookup"><span data-stu-id="a7421-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="a7421-153">İkili sınıflandırma kullanarak bir Web uygulamasındaki yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="a7421-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="a7421-154">Kodu kullanarak bir modele eğitim yapıyorsanız, [ml.NET API 'sini kullanarak nasıl veri yükleneceğini öğrenin](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="a7421-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
